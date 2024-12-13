

<template>
  <h1>Support</h1>
  <Input :changeAmount="changeAmount" />
  <div className="selectors">
    <Selector :setInfo="setInfoFirst" />
    <Selector :setInfo="setInfoSecond" />
  </div>
  {{ infoFirst }}
  {{ infoSecond }}
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
      infoSecond: ""
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
    }

  }
}

</script>
