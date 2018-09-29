<template>
  <div>
    <div class="search">
      <input class="search-input" type="text" placeholder="请输入城市" v-model="keyword">
    </div>
    <div class="search-content" ref="searchList" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" :key="item.id" v-for="item in list">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: 'CitySearch',
    mounted(){
      this.scroll = new BScroll(this.$refs.searchList)
    },
    data(){
      return {
        keyword:"",
        list:[],
        timer:null
      }
    },
    props:{
      cities:Object
    },
    computed:{
      hasNoData () {
        return !this.list.length
      }
    },
    watch:{
      keyword(){
        if(this.timer){
          clearTimeout(this.timer)
        }
        if(!this.keyword){
          this.list = [];
          return
        }
        this.timer = setTimeout(()=>{
          const result =[];
          for(let key in this.cities){
            this.cities[key].forEach((value)=>{
              if(value.spell.indexOf(this.keyword)>-1 || value.name.indexOf(this.keyword)>-1){
                result.push(value)
              }
            })
          }
          this.list = result
        },100)
      }
    }
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
  .search-content
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    bottom: 0
    right: 0
    background: #eee
    z-index:1
    .search-item
      line-height: .62rem
      padding-left: .2rem
      color: #666
      background: #fff
</style>
