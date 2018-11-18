<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <i class="iconfont back">&#xe609;</i>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      <router-link tag="div" to="/" class="abs">
        <i class="iconfont back">&#xe609;</i>
      </router-link>
      详情介绍      
    </div>
  </div>
</template>

<script>
export default {
  name: 'detailHeader',
  data() {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll() {
      const height = document.documentElement.scrollTop
      if(height > 60) {
        this.showAbs = false
        let opacity = 0
        opacity = height / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle.opacity = opacity
      }else {
        this.showAbs = true
      }
    }
  },
  activated() {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated() {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl';
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width .8rem
    line-height .8rem
    border-radius .4rem
    text-align center
    background rgba(0,0,0,.2)
    .back
      color #fff 
  .header-fixed
    position fixed
    top 0
    left 0
    right 0
    z-index 2 
    line-height .86rem
    text-align center
    color #fff
    background $bgColor
    .back
      position absolute
      left .1rem
      top .02rem
      padding: 0 .1rem
      width .64rem
      line-height .86rem

</style>


