<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <i class="iconfont header-back">&#xe609;</i>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "cityHeader"
};
</script>

<style lang="stylus" scoped>
@import '../../../assets/styles/varibles.styl';

.header {
  position: relative;
  overflow: hidden;
  height: 0.86rem;
  line-height: 0.86rem;
  text-align: center;
  color: #fff;
  background: $bgColor;

  .header-back {
    position: absolute;
    left: 0;
    top: 0;
    width: 0.64rem;
    text-align: center;
    font-size: 0.4rem;
    color: #fff;
  }
}
</style>
