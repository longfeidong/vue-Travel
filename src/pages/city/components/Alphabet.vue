<template>
  <div class="alphabet">
    <ul class="letter">
      <li>A</li>
      <li>C</li>
      <li>A</li>
      <li>C</li>
      <li>A</li>
      <li>C</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .letter
    display flex
    flex-direction column
    justify-content center
    align-items center
    width .4rem
    position absolute
    top 1.68rem
    right 0
    bottom 0
    li
      line-height .4rem
      color $darkTextColor
</style>
