<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}}
      <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
  import {mapState} from 'vuex'
  export default {
    name: 'HomeHeader',
    computed:{
      ...mapState(['city'])
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~Styles/varibles.styl"
  .header
    background: $bgColor
    display: flex
    height: $headerHeight
    line-height: $headerHeight
    justify-content:space-between
    color: #fff;
    .header-left
      /*float: left*/
      width: .64rem
      .back-icon
        text-align: center
        font-size:.4rem
    .header-input
      flex-grow:1
      background-color: #fff
      border-radius:.1rem
      margin-top: .12rem
      margin-left: .2rem
      height: .64rem
      color: #ccc
      line-height: .64rem
      padding-left: .2rem
    .header-right
      /*float: right*/
      min-width: 1.04rem
      padding 0 .1rem
      text-align: center
      color: #fff
      .arrow-icon
        font-size:.24rem
        margin-left: -.04rem;



</style>
