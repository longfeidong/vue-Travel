<template>
  <div class="header">
    <router-link tag="div" to="/" class="back-higher-ups">
      <span class="iconfont back-icon">&#xe624;</span>
    </router-link>
    <div class="header-fixed" v-show="isShow" :style="opacityStyle">
      <router-link to="/">
        <span class="iconfont back-home">&#xe624;</span>
      </router-link>
      长城
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      isShow: false,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 1) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.isShow = true
        this.opacityStyle = { opacity: opacity }
      } else {
        this.isShow = false
        this.opacityStyle = { opacity: 0 }
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    // 解绑全局事件，以免影响其它组件
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .back-higher-ups
    position absolute
    left .1rem
    top .1rem
    width .72rem
    height .72rem
    line-height .72rem
    text-align center
    background rgba(0, 0, 0, .5)
    border-radius 50%
    .back-icon
      font-size .36rem
      color #fff
  .header-fixed
    position fixed
    left 0
    top 0
    right 0
    height $headerHeight
    line-height $headerHeight
    background $bgColor
    overflow hidden
    font-size .32rem
    color #fff
    text-align center
    .back-home
      position absolute
      left .2rem
      top 0
      color #fff
</style>
