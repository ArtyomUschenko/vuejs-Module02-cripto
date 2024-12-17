

<template>
  <h1>Support</h1>
  <Input :changeAmount="changeAmount" :saveInfo="saveInfo" :favourite="favourite" />
  <br>
  <Favourite :favs="favs" v-if="favs.length > 0" :getFromFavs="getFromFavs" />
  <div className="selectors">
    <Selector :setInfo="setInfoFirst" :infoNow="infoFirst"/>
    <Selector :setInfo="setInfoSecond" :infoNow="infoSecond"/>
  </div>

  <p v-if="error != ''">{{ error }}</p>
  <p v-if="result != '0'" class="result-text">{{ result }}</p>

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
import Favourite from "./components/favourite.vue";
import CryptoConvert from 'crypto-convert'

const convert = new CryptoConvert();


export default {
  components: { Input, Selector, Favourite },
  data() {
    return {
      amount: 0,
      infoFirst: "",
      infoSecond: "",
      error: "",
      result: "0",
      favs: []
    }
  },
  methods: {
    favourite() {
      this.favs.push(
          {
            from: this.infoFirst,
            to: this.infoSecond,
      });
    },
    getFromFavs(index) {
      this.infoFirst = this.favs[index].from;
      this.infoSecond = this.favs[index].to;
    },

    changeAmount(val) {
      this.amount = val
    },
    setInfoFirst(val) {
      this.infoFirst = val
    },
    setInfoSecond(val) {
      this.infoSecond = val
    },
    async saveInfo() {
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
      await convert.ready();


      if(this.infoFirst == 'Система' && this.infoSecond == 'Организация') {
        this.result = convert.BTC.USD(this.amount)
      } else if (this.infoFirst == 'Система' && this.infoSecond == 'ФИО') {
        this.result = convert.BTC.ETH(this.amount)
      } else if (this.infoFirst == 'Организация' && this.infoSecond == 'ФИО') {
        this.result = convert.USD.ETH(this.amount)
      }else if (this.infoFirst == 'Организация' && this.infoSecond == 'Система') {
        this.result = convert.USD.BTC(this.amount)
      }else if (this.infoFirst == 'ФИО' && this.infoSecond == 'Система') {
        this.result = convert.ETH.BTC(this.amount)
      } else if (this.infoFirst == 'ФИО' && this.infoSecond == 'Организация'){
        this.result = convert.ETH.USD(this.amount)
      }

    }
  }
}

</script>
