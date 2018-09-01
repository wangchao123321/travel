<template>
  <div>
    <home-header :city="city"></home-header>
    <homeswiper :list="swiperList"></homeswiper>
    <HomeIcons :list="iconList"></HomeIcons>
    <HomeRecommend :list="recommendList"></HomeRecommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
  import HomeHeader from './compoments/Header'
  import Homeswiper from './compoments/swiper'
  import HomeIcons from './compoments/lcons'
  import HomeRecommend from './compoments/Recommend'
  import HomeWeekend from './compoments/Weekend'
  import axios from 'axios'
  export default {
    name: "Home",
    components: {
      HomeHeader,
      Homeswiper,
      HomeIcons,
      HomeRecommend,
      HomeWeekend
    },
    data () {
      return {
        city: '',
        swiperList: [],
        iconList: [],
        recommendList: [],
        weekendList: []
      }
    },
    methods: {
      getHomeInfo (){
        axios.get('/api/index.json').then(this.getHomeInfoSucc);
      },
      getHomeInfoSucc (res){
        res=res.data
        if(res.ret && res.data){
          const data=res.data
          this.city=data.city
          this.swiperList=data.swiperList
          this.iconList=data.iconList
          this.recommendList=data.recommendList
          this.weekendList=data.weekendList
        }
        console.log(res)
      }
    },
    mounted (){
      this.getHomeInfo();
    }
  }
</script>

<style>
</style>
