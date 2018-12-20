<template>
  <div class="wraper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item in bannerList" :key="item.id">
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
  data () {
    return {
      bannerList: [
        {
          id: 1001,
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1810/af/30ffcf34e9819f02.jpg_750x200_736b7236.jpg'
        },
        {
          id: 1002,
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1812/47/a51fe403715df102.jpg_750x200_085792b6.jpg'
        },
        {
          id: 1003,
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1812/92/edb99066ecb8ac02.jpg_750x200_059678c3.jpg'
        },
        {
          id: 1004,
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1812/d6/daa880b254940402.jpg_750x200_b114308a.jpg'
        }
      ],
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
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
