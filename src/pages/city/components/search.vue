<template>
  <div>
    <div class="search">
      <input type="text" placeholder="输入城市名或拼音" v-model="keyword">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有匹配的数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (city) {
      // this.$store.commit('editCity', city)
      this.editCity(city)
      this.$router.push('/')
    },
    // 将mutations中的editcity方法映射到组件的方法中，映射的名字为changeCity
    // ...mapMutations({
    //   'changeCity': 'editCity'
    // })
    // 映射名跟mutations中的名称相同就直接传一个数组即可
    ...mapMutations(['editCity'])
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .search
    padding 0 .2rem
    height .80rem
    background $bgColor
    input
      box-sizing border-box
      width 100%
      height .60rem
      line-height .60rem
      padding 0 .1rem
      border-radius .1rem
      text-align center
  .search-content
    overflow hidden
    position absolute
    left 0
    top 1.68rem
    right 0
    bottom 0
    z-index 1
    background #eee
    .search-item
      line-height .60rem
      padding-left .2rem
      background #fff
      color $darkTextColor
</style>
