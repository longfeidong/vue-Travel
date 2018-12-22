<template>
  <div class="wraper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <!-- slides -->
      <swiper-slide v-for="item in list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: 3000,
        loop: true
      }
    }
  },
  computed: {
    // swiper首次挂载时实际上用的Home组件中的[]数组数据，导致了得到数据渲染后，首页显示的最后一张图
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
  // 样式穿透，不在受scoped作用域限制
  .wraper >>> .swiper-pagination-bullet-active
    background #fff !important
  .wraper
    width 100%
    height 0
    // 750 / 400 = 1.875, 50% / 1.875 = 0.2667
    padding-bottom 26.67%
    overflow hidden
    background #ccc
    .swiper-img
      width 100%
</style>
