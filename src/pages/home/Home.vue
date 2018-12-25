<template>
  <div class="main-wrap">
    <home-header></home-header>
    <home-swiper :list="bannerList"></home-swiper>
    <home-icon :list="iconList"></home-icon>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
// 引入数据请求工具
import axios from 'axios'
// 引入vuex中的共享数据state
import { mapState } from 'vuex'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcon,
    HomeRecommend,
    HomeWeekend
  },
  computed: {
    ...mapState(['city'])
  },
  data () {
    return {
      bannerList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  methods: {
    getHomeData () {
      // 请求本地的mock数据，借助webpack做下转发
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeDataSuc)
    },
    getHomeDataSuc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.bannerList = data.bannerList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted () {
    // 组件挂载完成，记录下当前的城市
    this.lastCity = this.city
    // 组件挂载完成请求所有数据
    this.getHomeData()
  },
  activated () {
    // 使用keep-alive标签后，页面重新显示，activated就会被调用
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeData()
    }
  }
}
</script>

<style lang="stylus" scoped>
  .main-wrap
    background #f5f5f5
</style>
