<template>
  <div class="weekend">
    <h2>周末去哪儿</h2>
    <ul class="weeklist">
      <li class="item" v-for="item in list" :key="item.id">
        <div class="img-wrap">
          <img :src="item.imgUrl" :alt="item.title">
        </div>
        <p class="weekend-title">{{item.title}}</p>
        <p class="weekend-desc">{{item.desc}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .weekend
    h2
      height .80rem
      line-height .80rem
      font-size .28rem
      color #212121
      text-indent .30rem
    .item
      background #fff
      margin-bottom .1rem
      .img-wrap
        overflow hidden
        height 0
        padding-bottom 36.52%
        img
          width 100%
      .weekend-title
        height .48rem
        line-height .48rem
        text-indent .20rem
        margin-top .16rem
        font-size .28rem
        color #212121
        ellipsis()
      .weekend-desc
        height .40rem
        line-height .40rem
        text-indent .20rem
        font-size .24rem
        color #616161
        ellipsis()
</style>
