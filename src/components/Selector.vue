

<template>
 <ul>
   <li @click="setInfo('Система')" :className="infoNow == 'Система' ? 'active' : ''">Система</li>
   <li @click="setInfo('Организация')" :className="infoNow == 'Организация' ? 'active' : ''">Организация</li>
   <li @click="setInfo('ФИО')" :className="infoNow== 'ФИО' ? 'active' : ''">ФИО</li>
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
      },
      infoNow: {
        type: String,
        required: true
      }
    },
  }
</script>