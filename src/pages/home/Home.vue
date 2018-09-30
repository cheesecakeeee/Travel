<template>
  <div>
   <home-header  />  <!--:city="city"-->
    <home-swiper :list='swiperList' />
    <home-icons :list="iconList"/>
    <home-recommend :list="recommendList"/>
    <home-weekend :list="weekendList"/>
  </div>
</template>

<script>
  import HomeHeader from './components/Header'
  import HomeSwiper from './components/Swiper'
  import HomeIcons from './components/Icons'
  import HomeRecommend from './components/Recommend'
  import HomeWeekend from './components/Weekend'
  import axios from  'axios'



  export default {
    name: 'home',
    data(){
      return {
        // city:'',
        swiperList:[],
        iconList:[],
        recommendList:[],
        weekendList:[]
      }
    },
    components:{
      HomeHeader,
      HomeSwiper,
      HomeIcons,
      HomeRecommend,
      HomeWeekend
    },
    methods:{
      getHomeInfo(){
        axios.get('/api/index.json')
          .then(this.getHomeInfoSucc)
      },
      getHomeInfoSucc(res){
        res = res.data
        if(res.ret && res.data){
          const data = res.data
          this.city = data.city
          this.swiperList = data.swiperList
          this.iconList = data.iconList
          this.recommendList = data.recommendList
          this.weekendList = data.weekendList
        }

      }
    },
    mounted(){    //页面挂载el后执行getHomeInfo方法
      this.getHomeInfo()
    }

  }
</script>

<style scoped >

</style>
