<template>
  <div class="icon-wrap">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="icon" v-for="item in page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl" />
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcon',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pages () {
      // icon列表每页显示8条，这里借助二维数组的概念分别存放
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icon-wrap >>> .swiper-container
    height 0
    padding-bottom 56%
  .icon-wrap
    padding-top .1rem
    background #fff
    .icon
      overflow hidden
      height 0
      float left
      width 25%
      padding-bottom 25%
      // background red
      position relative
      text-align center
      .icon-img
        position absolute
        left 0
        top 0
        right 0
        bottom .44rem
        // background blue
        box-sizing border-box
        padding .1rem
        .icon-img-content
          height 100%
      .icon-desc
        position absolute
        left 0
        right 0
        bottom 0
        height .44rem
        line-height .44rem
        color $darkTextColor
        ellipsis()
</style>
