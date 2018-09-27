<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page,index) in pages" :key = 'index'>
        <div class="icon" v-for="item in page" :key="item.key">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl" alt="">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeIcons',
    data(){
      return {
        iconList:[
          {
            id:'0001',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
            desc:'景点门票哈哈哈哈'
          },
          {
            id:'0002',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
            desc:'水上乐园'
          },
          {
            id:'0003',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png',
            desc:'游乐场'
          },
          {
            id:'0004',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',
            desc:'海洋馆'
          },
          {
            id:'0001',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
            desc:'景点门票'
          },
          {
            id:'0002',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
            desc:'水上乐园'
          },
          {
            id:'0003',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png',
            desc:'游乐场'
          },
          {
            id:'0004',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',
            desc:'海洋馆'
          },
          {
            id:'0004',
            imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',
            desc:'海洋馆'
          }
        ]
      }
    },
    computed:{
      pages(){
        const pages = [];
        this.iconList.forEach((item,index)=>{
          const page  = Math.floor(index/8);
          if(!pages[page]){
            pages[page] = []
          }
          pages[page].push(item);
        })
        return pages
      }
    }
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/varibles.styl"
  @import "~Styles/mixins.styl"
  .icons >>> .swiper-container
    height:0
    padding-bottom:50%
  .icons
    margin-top: .1rem
    .icon
      overflow: hidden
      position: relative
      float: left
      width: 25%
      height: 0
      padding-bottom: 25%
      .icon-img
        position: absolute
        top: 0
        right: 0
        left:0
        bottom: .44rem
        box-sizing:border-box
        padding .1rem
        .icon-img-content
          display: block
          margin: 0 auto
          height: 100%
      .icon-desc
        position: absolute
        left: 0
        right: 0
        bottom: 0
        height:.44rem
        line-height: .44rem
        text-align: center
        color: $darkTextColor
        ellipsis()

</style>
