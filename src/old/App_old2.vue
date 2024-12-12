<template>
    <div class="wrapper">
      <h1>Приложение</h1>
      <p>Информация по ID: {{ id == "" ? "0000000": idName }}</p>
<!--      <input type="text" placeholder="ID" @input="this.id = $event.target.value">-->
          <input type="text" placeholder="Введите ID" v-model="id">
<!--      <button v-show="id != ''">Отправить</button>-->
      <button v-if="id != ''" @click="getInfo">Отправить</button>
      <button disabled v-else>Введите ID</button>
      <p class="error">{{ error}}</p>
      <div v-if="info != null">
              <p>{{ idStatus }}</p>
              <p>{{ idCode }}</p>
      </div>
    </div>
</template>

<style scoped>

.error {
  color: red;
  font-size: 18px;
  margin-top: 20px;
}


.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  padding: 20px;
  background-color: #f5f5f5;
  text-align: center;
}
.wrapper h1 {
  margin-top: 50px;
}
.wrapper p {
  margin-top: 20px;
}
.wrapper input {
  margin-top: 30px;
  background: transparent;
  border: 0;
  border-bottom: 1px solid rgba(105, 120, 141, 0.27);
  color: black;
  padding: 5px 8px;
  outline: none;
}
.wrapper input:focus {
  border-bottom: 1px solid rgba(194, 197, 201, 0.27);
}
.wrapper button {
  background: #e3bc4d;
  color: black;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 5px 5px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:disabled {
  background: #a08a49;
  cursor: not-allowed;
}


.wrapper button:hover {
 transform: scale(1.1) translateY(-5px);
}
</style>

<script>
import axios from 'axios'
import {compile} from "vue";



export default {
  data() {
    return {
      id: "",
      error : "",
      info: null
    }
  },
  computed:{
    idName() {
      return "«" + this.id + "»"
    },
    idStatus() {
      return this.info.base
    },
    idCode() {
      return this.info.cod
    }

  },
  methods: {
    compile,
    getInfo() {
      if(this.id.trim().length < 5) {
        this.error = "Введите корректный ID"
        return false
      }
      this.error = ""

      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.id}&units=metric&appid=99801ae26a4edeb80e6af2d2b78e3906`)
          // .then(res => (this.info = res))
          .then(res => (this.info = res.data))
          .catch(err => {
            this.error = "Ошибка загрузки данных: " + (err.response?.data?.message || "Неизвестная ошибка");
            this.info = null;
          });
    }
  }
}
</script>