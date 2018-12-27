<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailHeader from './components/Header'
import DetailBanner from './components/Banner'
import DetailList from './components/List'

export default {
  name: 'Detail',
  components: {
    DetailHeader,
    DetailBanner,
    DetailList
  },
  data () {
    return {
      list: [
        {
          id: '0001',
          title: '成人票',
          children: [
            {
              id: '1001',
              title: '成人票三馆联票',
              children: [
                {
                  id: '2001',
                  title: '成人票五馆联票，自营直销'
                }
              ]
            }
          ]
        },
        {
          id: '0002',
          title: '儿童票'
        },
        {
          id: '0003',
          title: '老人票'
        },
        {
          id: '0004',
          title: '特价票'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height 50rem
</style>
