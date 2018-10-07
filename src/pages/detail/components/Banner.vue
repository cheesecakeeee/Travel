<template>
    <div class="banner">
      <img  class="banner-img" src="//img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_600x330_f922b488.jpg" alt="">
      <div class="banner-info">
        <div class="banner-title">故宫(AAAAA景区)</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe6eb;</span>
          10
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        name: "DetailBanner"
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
