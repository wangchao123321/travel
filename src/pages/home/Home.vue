<template>
  <div>
    <home-header></home-header>
    <homeswiper></homeswiper>
  </div>
</template>

<script>
  import HomeHeader from './compoments/Header'
  import Homeswiper from './compoments/swiper'
  export default {
    name: "Home",
    components: {
      HomeHeader,
      Homeswiper},
  }
</script>

<style>
</style>
