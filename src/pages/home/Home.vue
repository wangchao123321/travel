<template>
  <div>
    <home-header></home-header>
    <homeswiper></homeswiper>
    <HomeIcons></HomeIcons>
    <HomeRecommend></HomeRecommend>
  </div>
</template>

<script>
  import HomeHeader from './compoments/Header'
  import Homeswiper from './compoments/swiper'
  import HomeIcons from './compoments/lcons'
  import HomeRecommend from './compoments/Recommend'
  export default {
    name: "Home",
    components: {
      HomeHeader,
      Homeswiper,
      HomeIcons,
      HomeRecommend
    }
  }
</script>

<style>
</style>
