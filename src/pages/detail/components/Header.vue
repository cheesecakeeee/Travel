<template>
    <div>
      <router-link
        tag="div"
        to="/"
        class="header-abs"
        v-show="showAbs"
      >
        <div class="iconfont header-abs-back">&#xe624;</div>
      </router-link>
      <div class="header-fixed"
           v-show="!showAbs"
           :style="opacityStyle"
      >
        <router-link to="/">
          <div  class="iconfont header-back">&#xe624;</div>
        </router-link>
        景点详情
      </div>
    </div>
</template>

<script>
  export default {
    name: "DetailHeader",
    data(){
      return {
        showAbs:true,
        opacityStyle:{
          opacity:0
        }
      }
    },
    methods:{
      handleScroll(){
        const top = document.documentElement.scrollTop
        if(top>60){
          let opacity = top /140
          opacity = opacity > 1 ? 1 : opacity
          this.opacityStyle = {opacity}
          this.showAbs = false
        }else {
          this.showAbs = true
        }
      }
    },
    activated(){
      window.addEventListener('scroll',this.handleScroll)
    }
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/varibles.styl"
  .header-abs
    position: absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    line-height: .8rem
    border-radius:.4rem
    background: rgba(0,0,0,.8)
    text-align: center
    .header-abs-back
      color: #ffffff
      font-size: .4rem
  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    height: $headerHeight
    line-height: $headerHeight
    color: #fff
    text-align: center
    background: $bgColor
    font-size: .32rem
    .header-back
      font-size:.4rem
      width: .64rem
      color: #fff
      position: absolute
      left: 0
      top: 0
</style>
