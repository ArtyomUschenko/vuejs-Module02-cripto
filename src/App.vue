

<template>
  <h1>Support</h1>
  <Input :changeAmount="changeAmount" :saveInfo="saveInfo"/>
  <div className="selectors">
    <Selector :setInfo="setInfoFirst" />
    <Selector :setInfo="setInfoSecond" />
  </div>
  <p v-if="error != ''">{{ error }}</p>
</template>

<style scoped>

.selectors {
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}


</style>

<script>
import Input from "./components/Input.vue"
import Selector from "./components/Selector.vue"

export default {
  components: { Input, Selector },
  data() {
    return {
      amount: 0,
      infoFirst: "",
      infoSecond: "",
      error: ""
    }
  },
  methods: {
    changeAmount(val) {
      this.amount = val
    },
    setInfoFirst(val) {
      this.infoFirst = val
    },
    setInfoSecond(val) {
      this.infoSecond = val
    },
    saveInfo() {
      if(this.amount <=0) {
        this.error = "Введите значения"
        return;
      }else if (this.infoFirst == this.infoSecond) {
        this.error = "Выберите разные значения"
        return;
      }else if (this.infoFirst == '' || this.infoSecond == '') {
        this.error = "Выберите значения"
        return;
      }
      this.error = ""
    }
  }
}

</script>
