<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="item in recommendList" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" class="item-img" alt="">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>


  </div>
</template>

<script>
  export default {
    name: 'HomeWeekend',
    data(){
      return {
        recommendList:[
          {
            id:'0001',
            imgUrl:'http://img1.qunarzz.com/sight/source/1505/b7/8a08a1023062b3.jpg_r_640x214_d7cb475c.jpg',
            title:'最赞的海滨浴场',
            desc:'哈哈哈哈哈哈哈哈哈哈或或或或哈哈哈哈哈哈哈哈哈哈'
          },
          {
            id:'0002',
            imgUrl:'http://img1.qunarzz.com/sight/source/1505/7f/fa4eb0ca72409d.jpg_r_640x214_2f2a860e.jpg',
            title:'大连必游TOP10',
            desc:'哈哈哈哈哈哈哈哈哈哈或或或或哈哈哈哈哈哈哈哈哈哈'
          },
          {
            id:'0003',
            imgUrl:'http://img1.qunarzz.com/sight/source/1507/6b/70d17d828d87e1.jpg_r_640x214_6a995270.jpg',
            title:'周末游首选',
            desc:'哈哈哈哈哈哈哈哈哈哈或或或或哈哈哈哈哈哈哈哈哈哈'
          }
        ]
      }
    }
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/mixins.styl"
  .title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent:.2rem
  .item-img-wrapper
    height: 0
    overflow: hidden
    padding-bottom:33.9%
    .item-img
      width: 100%
  .item-title
    line-height: .54rem
    font-size .32rem
    ellipsis()
  .item-desc
    line-height: .4rem
    color: #ccc
    ellipsis()


</style>
