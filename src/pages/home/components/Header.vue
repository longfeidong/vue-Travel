<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont back-icon">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont search-icon">&#xe632;</span>
      <span>输入城市/景点/游玩主题</span>
    </div>
    <router-link to="/city">
      <div class="header-right">
        <span>{{this.city}}</span>
        <span class="iconfont arrow-icon">&#xe6dc;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
  // css引用标识符需要加~
  @import '~styles/varibles.styl';
  /*
  1rem = 50px, 设计图是750px, 实际手机中是375，header部分的高度为88px, 实际应为 88/2 = 44px,
  换算成rem就是 44/50 = 0.88rem, 为了换算方便我们直接用量取到的高度值 88 / 100 = 0.88rem, 0可以省略
  */
  .header
    display flex
    line-height $headerHeight
    background $bgColor
    color #fff
    .header-left
      float left
      width .8rem
      .back-icon
        display block
        margin-left .2rem
    .header-input
      display flex
      flex 1
      height .6rem
      line-height .6rem
      margin .14rem 0 .14rem .2rem
      background #fff
      border-radius .1rem
      color #ccc
      .search-icon
        padding 0 .12rem 0 .2rem
    .header-right
      float right
      min-width 1.12rem
      padding 0 .1rem
      text-align center
      color #fff
      .arrow-icon
        font-size .24rem
</style>
