<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header></detail-header>
  </div>
</template>

<script>
import DetailHeader from './components/Header'
import DetailBanner from './components/Banner'

export default {
  name: 'Detail',
  components: {
    DetailHeader,
    DetailBanner
  }
}
</script>

<style lang="stylus" scoped>

</style>
