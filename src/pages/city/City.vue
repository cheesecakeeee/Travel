<template>
  <div>
    <city-header/>
    <city-search/>
    <city-list :hotCities = 'hotCities' :cities = 'cities'/>
    <city-alphabet :cities = 'cities'/>
  </div>
</template>

<script>
  import axios from 'axios'
  import CityHeader from './components/Header'
  import CitySearch from './components/Search'
  import CityList from './components/List'
  import CityAlphabet from './components/Alphabet'
  export default {
    name: 'City',
    methods:{
      getCityInfo(){
        axios.get('/api/city.json')
          .then(this.handleGetCityInfoSucc)
      },
      handleGetCityInfoSucc(res){
        res = res.data
        if(res.ret && res.data){
          const  data = res.data
          this.hotCities = data.hotCities
          this.cities = data.cities
        }
      }
    },
    data(){
      return {
        hotCities:[],
        cities:{}
      }
    },
    mounted(){
      this.getCityInfo()
    },
    components:{
      CityHeader,
      CitySearch,
      CityList,
      CityAlphabet
    }
  }
</script>

<style scoped lang="stylus">

</style>
