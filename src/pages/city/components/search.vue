<template>
  <div class="search">
    <input type="text" placeholder="输入城市名或拼音">
  </div>
</template>

<script>
export default {
  name: 'CitySearch'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .search
    padding 0 .2rem
    height .80rem
    background $bgColor
    input
      box-sizing border-box
      width 100%
      height .60rem
      line-height .60rem
      padding 0 .1rem
      border-radius .1rem
      text-align center
</style>
