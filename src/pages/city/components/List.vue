<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <h2 class="title border-topbottom">当前城市</h2>
        <ul class="city-list">
          <li class="city-list-item">
            <div class="city-button">{{this.currentCity}}</div>
          </li>
        </ul>
      </div>
      <div class="area">
        <h2 class="title border-topbottom">热门城市</h2>
        <ul class="city-list">
          <li class="city-list-item" v-for="item of hotCities" :key="item.id" @click="handleCityClick(item.name)">
            <div class="city-button">{{item.name}}</div>
          </li>
        </ul>
      </div>
      <div class="area" v-for="(itemArr, key) of cities" :key="key" :ref="key">
        <h2 class="title border-topbottom">{{key}}</h2>
        <ul class="initials-list">
          <li class="initials-list-item border-bottom" v-for="item of itemArr" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'

export default {
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleCityClick (city) {
      // this.$store.dispatch('changeCity', city)
      // 如果操作比较简单，非批量或异步操作，可以省略actions,直接commit
      // this.$store.commit('editCity', city)
      this.editCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['editCity'])
  },
  watch: {
    letter () {
      if (this.letter) {
        // 滚动到哪个元素
        const element = this.$refs[this.letter][0]
        // 调用better-scroll下面的滚动到指定元素的方法
        this.scroll.scrollToElement(element)
      }
    }
  },
  mounted () {
    // 必须获取组件最外层的父级元素才生效
    this.scroll = new BScroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-topbottom
    &:before
      border-color #777
    &:after
      border-color #777
  .border-bottom
    &:before
      border-color #777
  .list
    position absolute
    left 0
    top 1.68rem
    right 0
    bottom 0
    overflow hidden
    .title
      line-height .76rem
      background #f5f5f5
      padding-left .20rem
      color $darkTextColor
      font-size .24rem
    .city-list
      overflow hidden
      padding .1rem .6rem .1rem .1rem
      .city-list-item
        float left
        width 33.33%
        .city-button
          padding .1rem 0
          margin .1rem
          border .02rem solid #CCC
          border-radius .06rem
          text-align center
          color $darkTextColor
    .initials-list
      .initials-list-item
        line-height .76rem
        padding-left .2rem
        color $darkTextColor
</style>
