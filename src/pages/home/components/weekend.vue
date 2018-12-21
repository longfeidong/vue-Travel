<template>
  <div class="weekend">
    <h2>周末去哪儿</h2>
    <ul class="weeklist">
      <li class="item" v-for="item in weekendList" :key="item.id">
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
  data () {
    return {
      weekendList: [
        {
          id: 1001,
          imgUrl: 'http://img1.qunarzz.com/sight/source/1811/f3/86173f863bef61.jpg_r_640x214_52b003ac.jpg',
          title: '京城周末撒欢',
          desc: '在帝都过周末，不仅仅是城中游！'
        },
        {
          id: 1002,
          imgUrl: 'http://img1.qunarzz.com/sight/source/1510/6e/1ea71e2f04e.jpg_r_640x214_aa6f091d.jpg',
          title: '京城有好泉',
          desc: '细数北京温泉，温暖你的冬天'
        },
        {
          id: 1003,
          imgUrl: 'http://img1.qunarzz.com/sight/source/1811/7e/476589267ebb41.jpg_r_640x214_bf599709.jpg',
          title: '京城溜娃必去',
          desc: '德智体美劳全面发展的亲子日，这些地方该去看看…'
        }
      ]
    }
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
