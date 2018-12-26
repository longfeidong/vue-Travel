<template>
  <div class="gallary" @click="handleClickClose">
    <div class="wraper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(item, index) of imgs" :key="index">
          <img :src="item" alt="">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handleClickClose () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .gallary >>> .swiper-container
    overflow inherit
  .gallary
    display flex
    flex-direction column
    justify-content center
    position absolute
    left 0
    top 0
    right 0
    bottom 0
    z-index 99
    background #000
    .wraper
      width 100%
      height 0
      padding-bottom 66.75%
      img
        width 100%
      .swiper-pagination
        color #fff
        bottom -1rem
</style>
