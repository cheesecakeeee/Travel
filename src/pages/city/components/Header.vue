<template>
  <div class="header">
    选择城市
    <router-link to="/">
      <div  class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
  export default {
    name: 'CityHeader'
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/varibles.styl"
  .header
    position: relative
    height: $headerHeight
    line-height: $headerHeight
    overflow: hidden
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
