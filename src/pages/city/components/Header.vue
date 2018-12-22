<template>
  <div class="header">
    <router-link to="/">
      <span class="iconfont back-home">&#xe624;</span>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    height $headerHeight
    line-height $headerHeight
    background $bgColor
    overflow hidden
    font-size .32rem
    color #fff
    text-align center
    position relative
    .back-home
      position absolute
      left .2rem
      top 0
      color #fff
</style>
