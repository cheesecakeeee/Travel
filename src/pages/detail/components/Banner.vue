<template>
    <div>
      <div class="banner" @click="handleBannerClick">
        <img  class="banner-img" :src="this.bannerImg" alt="">
        <div class="banner-info">
          <div class="banner-title">{{this.sightName}}</div>
          <div class="banner-number">
            <span class="iconfont banner-icon">&#xe6eb;</span>
            10
          </div>
        </div>
      </div>
      <common-gallery
        :imgs="this.gallaryImgs"
        v-show="showGalley"
        @close="handleGalleryClose"
      />
    </div>
</template>

<script>
  import CommonGallery from 'common/gallery/Gallery'
  export default {
    name: "DetailBanner",
    components:{
      CommonGallery
    },
    data(){
      return {
        showGalley:false,
      }
    },
    methods:{
      handleBannerClick(){
        this.showGalley = true
      },
      handleGalleryClose(){
        this.showGalley = false
      }
    },
    props:{
      sightName:String,
      bannerImg:String,
      gallaryImgs:Array,
    }
  }
</script>

<style scoped lang="stylus">
  .banner
    overflow: hidden
    height: 0
    padding-bottom: 55%
    background: #eee
    position: relative
    .banner-img
      width: 100%
    .banner-info
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      display: flex
      color: #fff
      background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
      .banner-title
        flex:1
        font-size .32rem
        padding:0 .2rem
      .banner-number
        height: .32rem
        line-height:.32rem
        margin-top: .2rem
        padding 0 .4rem
        border-radius:.2rem
        background: rgba(0,0,0,.8)
        font-size:.24rem
        .banner-icon
          font-size:.24rem


</style>
