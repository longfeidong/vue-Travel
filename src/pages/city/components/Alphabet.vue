<template>
  <div class="alphabet">
    <ul class="letter">
      <!-- <li v-for="item of letters" :key="item">{{item}}</li> -->
      <li
        v-for="item of letters"
        :key="item"
        :ref="item"
        @touchstart="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        @click="handleClickLetter"
      >
        {{item}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      // 定义touch开关
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    /*
      TouchMove里的代码执行频率很高，this.$refs['A'][0].offsetTop会反复执行，为了性能优化，提到updated里
      组件首次渲染时，父组件city的cities数据是个{}，当ajax获取数据后，数据发生改变updated就会执行
    */
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleClickLetter (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 84
          // 计算出当前手指滑动的位置所对应的字母的下标
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
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
