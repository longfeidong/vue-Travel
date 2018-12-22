<template>
  <div class="recommend">
    <div class="title">
      <span class="iconfont xin">&#xe6cd;</span>
      <h2>热销推荐</h2>
    </div>
    <ul class="rlist">
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="img-wrap">
          <img :src="item.imgUrl" :alt="item.title" />
        </div>
        <div class="info">
          <p class="info-title">{{item.title}}</p>
          <div class="info-comment">
            <span class="info-grade-box">
              <strong class="iconfont info-grade" :style="{width: item.grade}">&#xe631;</strong>
              <strong class="iconfont info-grade2">&#xe631;</strong>
            </span>
            <span class="info-comment-num">{{item.commentNum}}条评论</span>
          </div>
          <p class="info-price">
            <span class="prices">
              <span>￥<em>{{item.price}}</em></span>起
            </span>
            <span class="info-address">{{item.address}}</span>
          </p>
          <div class="info-feature" v-if="item.desc">{{item.desc}}</div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  },
  mounted () {
    this.list.forEach((item, index) => {
      item['grade'] = (item['grade'] / 5) * 100 + '%'
    })
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend
    margin-top .2rem
    background: #fff
    .title
      display flex
      align-items center
      padding-left .3rem
      ellipsis()
      .xin
        color #ff2134
      h2
        padding .2rem .15rem
        font-size .3rem
    .rlist
      padding-left .3rem
      .item
        display flex
        padding .24rem 0
        .img-wrap
          // overflow hidden
          // width 27.77%
          // height 0
          // padding-bottom 50%
          width 2rem
          height 2rem
          overflow hidden
          img
            width 100%
        .info
          flex 1
          padding-left .2rem
          min-width 0
          .info-title
            margin-top .25rem
            height .44rem
            line-height .44rem
            font-size .3rem
            ellipsis()
          .info-comment
            display flex
            height .5rem
            line-height .5rem
            align-items center
            .info-grade-box
              position relative
              width 1.3rem
              height 100%
              .info-grade
                position absolute
                left 0
                top 0
                z-index 2
                color #ffb436
                overflow hidden
              .info-grade2
                position absolute
                left 0
                top 0
                z-index 1
                color #e0e0e0
                overflow hidden
            .info-comment-num
              font-size .24rem
              color #616161
              margin-left .3rem
          .info-price
            display flex
            justify-content space-between
            align-items: center
            font-size .24rem
            padding .2rem 0
            .prices
              span
                color #ff8300
                em
                  font-size .4rem
            .info-address
              color #333
              margin-right .3rem
          .info-feature
            display inline-block
            height .36rem
            line-height .36rem
            padding 0 .1rem
            margin-top .4rem
            background #fff9f9
            color #f55
            font-size .24rem
</style>
