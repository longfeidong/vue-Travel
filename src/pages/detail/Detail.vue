<template>
  <div>
    <detail-banner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="categoryList"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailHeader from './components/Header'
import DetailBanner from './components/Banner'
import DetailList from './components/List'
import axios from 'axios'

export default {
  name: 'Detail',
  components: {
    DetailHeader,
    DetailBanner,
    DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      categoryList: []
    }
  },
  methods: {
    getDetailData () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getDetailDataSuc)
    },
    getDetailDataSuc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.categoryList = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailData()
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height 50rem
</style>
