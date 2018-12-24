<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
    <city-list :hotCities="hotCities" :cities="cities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="handleChangeLetter"></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'

export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  methods: {
    getCityData () {
      axios.get('/api/city.json')
        .then(this.getCityDataSuc)
    },
    getCityDataSuc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.hotCities = data.hotCities
        this.cities = data.cities
        // for (const key in data.cities) {
        //   if (data.cities.hasOwnProperty(key)) {
        //     this.letter.push(key)
        //   }
        // }
      }
    },
    handleChangeLetter (letter) {
      // 接收到子组件Alphabet的信息，通过绑定属性传给子组件list
      this.letter = letter
    }
  },
  mounted () {
    this.getCityData()
  }
}
</script>

<style lang="stylus" scoped>

</style>
