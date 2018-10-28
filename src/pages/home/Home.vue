<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <p>ddd</p>
  </div>

</template>

<script>
import homeHeader from './components/Header'
import homeSwiper from './components/Swiper'
export default {
  name: 'home',
  components: {
    homeHeader,
    homeSwiper
  }
}
</script>

<style lang="stylus" scoped>

</style>

