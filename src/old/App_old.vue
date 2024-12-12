<template>
  <input type="text" @input="insertData($event.target.value)" placeholder="Имя">
  <input type="password" v-model="userPass" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">
  <button @click="sendData">Отправить</button>
  <p> {{ userName}} </p>
  <p> {{ userPass }} </p>
  <p> {{ userEmail }} </p>
  <p> {{ users }}</p>
  <p className="error"> {{ error }}</p>
  <div v-for="(el, index) in users" :key="index">
 <h3>Имя: {{ el.name }}</h3>
  <p>Email: {{ el.email }}</p>
  </div>

  <div v-if="users.length == 0">
    У нас нет пользователей
  </div>

  <div v-else-if="users.length == 1">
    В базе один пользователь
  </div>

  <div v-else="users.length > 1">
    В базе есть пользователи и больше одного
  </div>
</template>

<style scoped>
</style>

<script>
  export default {
    data() {
      return {
        users: [],
        userName: "",
        userPass: "",
        userEmail: "",
        error: ""
      }
    },
    methods: {
        insertData(val) {
          this.userName = val
        },
        sendData() {
          if(this.userName == "") {
            this.error = "Введите имя";
            return;
          }
          else if (this.userEmail == "") {
            this.error = "Введите email";
            return;
          }

          this.error = "";

          this.users.push({
            name: this.userName,
            pass: this.userPass,
            email: this.userEmail
          })
        }
      }
    }
</script>