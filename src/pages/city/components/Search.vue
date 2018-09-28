<template>
  <div class="search">
    <input class="search-input" type="text" placeholder="请输入城市">
  </div>
</template>

<script>
  export default {
    name: 'CitySearch'
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/varibles.styl"
  .search
    height: .72rem
    padding:0 .1rem
    background:$bgColor
    .search-input
      width: 100%
      height: .62rem
      line-height: .62rem
      box-sizing:border-box
      padding 0 .1rem
      text-align: center
      color: #666
      border-radius:.06rem
</style>
