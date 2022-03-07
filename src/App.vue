<template>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
  <div id="app" class="">
    <main-menu></main-menu>
  </div>
</template>

<script>
import mainMenu from './components/mainMenu.vue'

export default {
  name: 'App',
  components:{
    mainMenu
  }
}
</script>

<style scoped>
#app{
   background-image: linear-gradient(180deg, hsla(218, 23%, 21%, 0.8) 30%, hsla(12, 83%, 62%, 0.5) 100%),url('~@/assets/index.png');
    background-repeat: no-repeat;
    background-size: contain;
    background-position:center;
    height: 100vh;
}
</style>
