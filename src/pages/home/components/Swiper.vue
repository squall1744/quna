<template>
  <div class="wrapper">
  <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="item in swiperList" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl" alt="">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
  </div>
</template>

<script>
export default {
  name: "carrousel",
  props: {
    swiperList: Array
  },
  data() {
    return {
      // NotNextTick is a component's own property, and if notNextTick is set to true, the component will not instantiate the swiper through NextTick, which means you can get the swiper object the first time (if you need to use the get swiper object to do what Things, then this property must be true)
      // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
      notNextTick: true,
      swiperOption: {
        // swiper options 所有的配置同swiper官方api配置
        autoplay: 3000,
        autoplayDisableOnInteraction: false,
        grabCursor: true,
        setWrapperSize: true,
        pagination: ".swiper-pagination",
        loop: true,
        paginationClickable: true,
        mousewheelControl: false,
        observeParents: true
        // if you need use plugins in the swiper, you can config in here like this
        // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
      }
    };
  },
  computed: {
    showSwiper() {
      return this.swiperList.length;
    }
  }
};
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active {
  background: #fff;
}

.wrapper {
  overflow: hidden;
  width: 100%;
  height: 0;
  padding-bottom: 31.25%;

  .swiper-img {
    width: 100%;
  }
}
</style>


