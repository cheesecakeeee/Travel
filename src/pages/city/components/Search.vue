<template>
  <div>
    <div class="search">
      <input class="search-input" type="text" placeholder="请输入城市" v-model="keyword">
    </div>
    <div class="search-content" ref="searchList" v-show="keyword">
      <ul>
        <li class="search-item border-bottom"
            :key="item.id"
            v-for="item in list"
            @click="handleCityClick(item.name)"
        >{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  import { mapMutations } from 'vuex'
  export default {
    name: 'CitySearch',
    mounted(){
      this.scroll = new BScroll(this.$refs.searchList)
    },
    data(){
      return {
        keyword:"", //关键词双向绑定
        list:[],  //存放搜索结果，初始结果为空
        timer:null  //延迟操作
      }
    },
    props:{
      cities:Object //遍历城市接口的所有数据，按需加入list
    },
    computed:{
      hasNoData () {
        return !this.list.length
      }
    },
    watch:{   //监听关键词的变化
      keyword(){
        if(this.timer){ //防止搜索越来越快，清空定时器
          clearTimeout(this.timer)
        }
        if(!this.keyword){  //如果关键词为空，则将搜索结果的data置空
          this.list = [];
          return
        }
        this.timer = setTimeout(()=>{ //延迟搜索
          const result =[];
          for(let key in this.cities){  //遍历对象的key
            this.cities[key].forEach((value)=>{ //根据key遍历对象数组中的每一个数组
              if(value.spell.indexOf(this.keyword)>-1 || value.name.indexOf(this.keyword)>-1){  //如果存在拼写活名字相同的值
                result.push(value)  //将满足名字活拼写相同的数据push到一个数组中
              }
            })
          }
          this.list = result  //将搜索结果数组赋值给data中的list，以便于遍历展示在也页面
        },100)
      }
    },
    methods:{
      handleCityClick(cityname){
        // this.$store.commit('changeCity',cityname)
        this.changeCity(cityname)
        this.$router.push('/')
      },
      ...mapMutations(['changeCity'])
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
