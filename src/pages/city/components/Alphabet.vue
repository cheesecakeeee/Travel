<template>
  <ul class="list">
    <li @click='handleLetterClick'
        class="item"
        v-for="item in  letters"
        :key="item"
        @touchstart.prevent = 'handleTouchStart'
        @touchmove = 'handleTouchMove'
        @touchend = 'handleTouchEnd'
        :ref = 'item'
    >
      {{item}}
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'CityAlphabet',
    props:{
      cities:Object
    },
    computed:{
      letters(){
        const letters = []
        for(let i in this.cities){
          letters.push(i)
        }
        return letters
      }
    },
    data(){
      return {
        touchStatus:false,
        aStartY:0,
        timer:null
      }
    },
    updated(){
      this.aStartY = this.$refs['A'][0].offsetTop
    },
    methods:{
      handleLetterClick(e){
        // console.log(e.target.innerText)
        this.$emit('change',e.target.innerText)
      },
      handleTouchStart(){
        this.touchStatus = true
      },
      handleTouchMove(e){
        if(this.touchStatus){
         if(this.timer){
           clearTimeout(this.timer)
         }
         setTimeout(()=>{
           const touchY = e.touches[0].clientY-79
           const index=  Math.floor((touchY-this.aStartY)/20)
           if(index>=0 && index<this.letters.length){
             this.$emit('change',this.letters[index])
           }
         },16)
        }
      },
      handleTouchEnd(){
        this.touchStatus = false
      }
    }
  }
</script>

<style scoped lang="stylus">
  @import "~Styles/varibles.styl"
  .list
    display: flex
    flex-direction:column
    justify-content:center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .item
      text-align: center
      line-height: .4rem
      color: $bgColor



</style>
