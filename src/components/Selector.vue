

<template>
 <ul>
   <li @click="selectItem('Система')" :className="active == 'Система' ? 'active' : ''">Система</li>
   <li @click="selectItem('Организация')" :className="active == 'Организация' ? 'active' : ''">Организация</li>
   <li @click="selectItem('ФИО')" :className="active == 'ФИО' ? 'active' : ''">ФИО</li>
 </ul>
</template>

<style scoped>
  ul {
    list-style: none;
    width: 200px;
    padding: 0;
    border-radius: 3px;
    border: 3px solid black;
  }
  li {
    display: block;
    background: black;
    color: white;
    padding: 20px 0;
  }

  li:hover, li.active {
    background: #282424;
    cursor: pointer;
  }

</style>


<script>
  export default {
    props: {
      setInfo: {
        type: Function,
        required: true
      }
    },
    data() {
      return {
        active: ""
      }
    },
    methods: {
      selectItem(val) {
        this.setInfo(val);
        this.active = val;
      }
    }
  }
</script>