<template>
  <div>
    <div class="banner" @click="handleClickDetail">
      <div class="back-higher-ups">
        <span class="iconfont back-icon">&#xe624;</span>
      </div>
      <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/1708/2b/2b3b94de99c0a425a3.img.jpg_600x330_b40971b4.jpg" alt="">
      <div class="banner-info">
        <div class="banner-album">
          <span class="iconfont">&#xe600;</span>
          <span class="album-num">13</span>
        </div>
        <p class="banner-spot">八达岭长城(AAAAA景区)</p>
      </div>
    </div>
    <common-gallary :imgs="imgs" v-show="showDetail"  @close="handleCloseGallary"></common-gallary>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  data () {
    return {
      showDetail: false,
      imgs: ['http://img1.qunarzz.com/sight/p0/1708/2b/2b3b94de99c0a425a3.img.jpg_r_800x800_ae28174d.jpg', 'http://img1.qunarzz.com/sight/p0/1803/f9/f96ac7520e964ad4a3.img.jpg_r_800x800_93b843b1.jpg']
    }
  },
  components: {
    CommonGallary
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
    .back-higher-ups
      position absolute
      left .1rem
      top .1rem
      right 0
      width .72rem
      height .72rem
      line-height .72rem
      text-align center
      background rgba(0, 0, 0, .5)
      border-radius 50%
      .back-icon
        font-size .36rem
        color #fff
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
