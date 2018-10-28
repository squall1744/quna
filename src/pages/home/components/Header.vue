<template>
  <div class="header">
    <div class="header-left">
      <i class="iconfont">&#xe609;</i>
    </div>
    <div class="header-input"><i class="iconfont">&#xe668;</i>输入城市/景点/游玩主题</div>
    <div class="header-right">城市<i class="iconfont">&#xe6e9;</i></div>
  </div>
</template>

<script>
export default {
  name: 'homeHeader'
}
</script>

<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .header
    font-size 12px
    display: flex
    line-height: .86rem
    background-color $bgColor 
    color #fff
    .header-left
      width: .64rem
    .header-input
      flex 1
      background #fff
      border-radius .1rem 
      line-height .64rem
      height .64rem
      margin-top .12rem
      margin-left .2rem
      color #ccc
    .header-right
      width 1.24rem
      text-align center
</style>

