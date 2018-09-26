<template>
  <div class="wrapper">
    <swiper :options="swiperOption" >
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="" />
      </swiper-slide>

      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeSwiper',
    data (){
      return {
        swiperOption:{
          pagination:'.swiper-pagination',
          loop:true
        },
        swiperList:[
          {
            id:'0001',
            imgUrl:"http://img1.qunarzz.com/piao/fusion/1809/28/869966be5963e102.jpg_750x200_f23248ba.jpg"
          },
          {
            id:'0002',
            imgUrl:"http://img1.qunarzz.com/piao/fusion/1805/e8/14b75b1c81fbe702.jpg_750x200_e6d4f1f1.jpg"
          },
          {
            id:'0003',
            imgUrl:"http://img1.qunarzz.com/piao/fusion/1807/66/e5a5cec881702f02.jpg_750x200_67bb5691.jpg"
          }
        ]
      }
    }
  }
</script>

<style scoped lang="stylus">
  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff
  .wrapper
    width: 100%
    height: 0
    overflow: hidden
    padding-bottom: 26.66%;
    background: #ee9b4c
    .swiper-img
      width: 100%

</style>
