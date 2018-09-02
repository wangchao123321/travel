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
  import { mapState } from 'vuex'
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
        lastCity: '',
        swiperList: [],
        iconList: [],
        recommendList: [],
        weekendList: []
      }
    },
    computed: {
      ...mapState(['city'])
    },
    methods: {
      getHomeInfo (){
        axios.get('/api/index.json?city='+ this.city).then(this.getHomeInfoSucc);
      },
      getHomeInfoSucc (res){
        res=res.data
        if(res.ret && res.data){
          const data=res.data
          this.swiperList=data.swiperList
          this.iconList=data.iconList
          this.recommendList=data.recommendList
          this.weekendList=data.weekendList
        }
        console.log(res)
      }
    },
    mounted (){
      this.lastCity=this.city
      this.getHomeInfo();
    },
    activated (){
    if(this.lastCity !== this.city){
      this.lastCity=this.city
      this.getHomeInfo()
    }
    }
  }
</script>

<style>
</style>
