<template>
  <div>
    <div class="banner" @click="handleClickDetail">
      <img class="banner-img" :src="bannerImg" alt="">
      <div class="banner-info">
        <div class="banner-album">
          <span class="iconfont">&#xe600;</span>
          <span class="album-num">{{gallaryImgs.length}}</span>
        </div>
        <p class="banner-spot">{{sightName}}</p>
      </div>
    </div>
    <fade-animation>
      <common-gallary :imgs="gallaryImgs" v-show="showDetail"  @close="handleCloseGallary"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showDetail: false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleClickDetail () {
      this.showDetail = true
    },
    handleCloseGallary () {
      this.showDetail = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    &:after
      content: ' '
      position: absolute
      left: 0
      right: 0
      bottom: 0
      height: .6rem
      color: #fff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
    .banner-img
      width 100%
    .banner-info
      position absolute
      left .2rem
      bottom .6rem
      right 0
      color #fff
      .banner-album
        display flex
        width 1.2rem
        height .4rem
        justify-content center
        align-items center
        font-size .24rem
        background rgba(226, 14, 14, .5)
        border-radius .2rem
        .iconfont
          font-size .24rem
        .album-num
          margin-left .1rem
      .banner-spot
        height .4rem
        line-height .4rem
        font-size .36rem
        margin-top .16rem
</style>
