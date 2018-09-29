<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item in hotCities" :key="item.id">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area"  v-for="(item,key) in cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="innerItem in item" :key="innerItem.id">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: 'CityList',
    mounted(){
      this.scroll = new BScroll(this.$refs.wrapper)
    },
    props:{
      hotCities:Array,
      cities:Object,
      allLetter:String
    },
    watch:{
      allLetter(){
        // console.log(this.allLetter)
        if(this.allLetter){
          const  Element  = this.$refs[this.allLetter][0];
          // console.log(Element)
          this.scroll.scrollToElement(Element)

        }

      }
    }
  }
</script>

<style scoped lang="stylus">
  .border-topbottom
    &:before
      boreder-color:#ccc
    &:after
      background-color #ccc
  .border-bottom
  &:before
    boreder-color:#ccc
  .list
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    bottom: 0
    right: 0
    .title
      line-height: .54rem
      background: #eee
      padding-left: .2rem
      font-size:.26rem
      color:#666
    .button-list
      padding:.1rem .6rem .1rem .1rem
      overflow: hidden
      .button-wrapper
        width: 33.33%
        float: left
        .button
          padding .1rem 0
          margin .1rem
          border: .02rem solid #ccc
          text-align: center
          border-radius .06rem

    .item-list
      .item
        line-height: .76rem
        padding-left: .2rem


</style>
