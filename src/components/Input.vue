
<template>
  <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Введите номер тикета"></input>
  <button @click="saveInfo">Добавить</button>
</template>

<style scoped>

input {
  width: 500px;
  font-size: 1.2em;
  position: relative;
  top: -50px;
  border-radius: 3px;
  border: 0;
  padding: 10px 15px;
  background-color: #f1f1f1;
  color: black;
  outline: none;
}
button {
  display: block;
  position: relative;
  top: -15px;
  padding: 15px 20px;
  color: white;
  text-transform: uppercase;
  background-color: black;
  margin: 0 auto;
  border: 0;
  border-radius: 25px;
}

</style>

<script>
export default {
  props: {
    changeAmount: {
      type: Function,
      required: true
    },
    saveInfo: {
      type: Function,
      required: true
    }
  }
}
</script>