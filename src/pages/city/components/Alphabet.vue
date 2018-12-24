<template>
  <div class="alphabet">
    <ul class="letter">
      <!-- <li v-for="item of letters" :key="item">{{item}}</li> -->
      <li v-for="(item, key) of cities" :key="key">{{key}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (const key in this.cities) {
        letters.push(key)
      }
      return letters
    }
  }
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
