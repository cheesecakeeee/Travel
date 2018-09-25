<template>
  <div class="header">
    <div class="header-left">返回</div>
    <div class="header-input">内容</div>
    <div class="header-right">城市</div>
  </div>
</template>

<script>
  export default {
    name: 'HomeHeader'
  }
</script>

<style lang="stylus" scoped>
  .header
    background-color: #00bcd4
    display: flex
    height .86rem
    .header-left
      float: left
      width: .64rem
    .header-input
      flex:1
    .header-right
      float: right
      width: 1.24rem



</style>
