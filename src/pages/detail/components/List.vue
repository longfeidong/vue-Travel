<template>
  <ul class="list">
    <li class="item border-bottom" v-for="item of list" :key="item.id">
      <span class="item-icon"></span>
      <span class="item-content">{{item.title}}</span>
      <div v-if="item.children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item
    line-height .6rem
    padding-left .2rem
    .item-icon
      display inline-block
      position relative
      left 0
      top .1rem
      width: .36rem;
      height: .36rem;
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
      margin-right: .1rem;
      background-size: .4rem 3rem;
</style>
