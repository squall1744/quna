<template>
  <div class="header">
    <div class="header-left">
      <i class="iconfont">&#xe609;</i>
    </div>
    <div class="header-input"><i class="iconfont">&#xe668;</i>输入城市/景点/游玩主题</div>
    <router-link to="/city">
      <div class="header-right">{{this.$store.state.city}}<i class="iconfont">&#xe6e9;</i></div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "homeHeader"
};
</script>

<style lang="stylus" scoped>
@import '../../../assets/styles/varibles.styl';

.header {
  font-size: 12px;
  display: flex;
  line-height: 0.86rem;
  background-color: $bgColor;
  color: #fff;

  .header-left {
    width: 0.64rem;
  }

  .header-input {
    flex: 1;
    background: #fff;
    border-radius: 0.1rem;
    line-height: 0.64rem;
    height: 0.64rem;
    margin-top: 0.12rem;
    margin-left: 0.2rem;
    color: #ccc;
  }

  .header-right {
    width: 1.24rem;
    text-align: center;
    color: #fff;
  }
}
</style>
