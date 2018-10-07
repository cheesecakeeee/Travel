<template>
  <div class="container" @click="handleGalleryClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide
          v-for="(item,index) of imgs"
          :key="index"
        >
          <img class="gallery-img" :src="item" alt="" />
        </swiper-slide>

        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>

  export default {
    name: "CommonGallery",
    data(){
      return {
        swiperOption:{
          pagination:'.swiper-pagination',
          paginationType:'fraction',
          observer:true,
          observeParents:true,
        }
      }
    },
    props:{
      imgs:{
        type:Array,
        default:[]
      }
    },
    methods:{
      handleGalleryClick(){
        this.$emit("close")
      }
    }

  }
</script>

<style scoped lang="stylus">
  .container >>> .swiper-container
    overflow:inherit
  .container
    display: flex
    flex-direction: column
    justify-content:center
    position: fixed
    top: 0
    left: 0
    right: 0
    bottom: 0
    background: #000
    z-index: 99
    .wrapper
      width: 100%
      .gallery-img
        width: 100%
      .swiper-pagination
        color: #fff
        bottom:-1rem

</style>
