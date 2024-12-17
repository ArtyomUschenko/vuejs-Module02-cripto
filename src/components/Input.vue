
<template>
  <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Введите номер тикета"></input>
  <button @click="saveInfo()">Добавить</button>
  <button @click="favourite" className="fav-button">В избранное</button>
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
  display: block;
  margin: 0 auto;
}
button {
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
button.fav-button {
  margin-left: 10px;
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
    },
    favourite: {
      type: Function,
      required: true
    },
  }
}
</script>