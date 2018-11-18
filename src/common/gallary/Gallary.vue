<template>
  <div class="container" @click="$emit('close')">
  <div class="wrapper">
  <swiper 
    :options="swiperOption" 
    :not-next-tick="notNextTick" 
    ref="mySwiper"
    v-if="showGallary"
  >
    <!-- slides -->
    <swiper-slide
      v-for="(item, index) in imgs"
      :key="index"
    >
      <img class="gallary-img" :src="item">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
  </div>
  </div>
</template>

<script>
export default {
  name: "gallary",
  props: {
    imgs: Array
  },
  data() {
    return {
      // NotNextTick is a component's own property, and if notNextTick is set to true, the component will not instantiate the swiper through NextTick, which means you can get the swiper object the first time (if you need to use the get swiper object to do what Things, then this property must be true)
      // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
      notNextTick: true,
      swiperOption: {
        // swiper options 所有的配置同swiper官方api配置
        // autoplay: 2000,
        // autoplayDisableOnInteraction: false,
        grabCursor: true,
        setWrapperSize: true,
        pagination: ".swiper-pagination",
        loop: true,
        paginationClickable: true,
        paginationType: "fraction",
        mousewheelControl: false,
        observeParents: true,
        observe: true
        // if you need use plugins in the swiper, you can config in here like this
        // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
      }
    };
  },
  methods: {
    showGallary() {
      return this.imgs.length;
    }
  }
};
</script>

<style lang="stylus" scoped>
.container >>> .swiper-container {
  overflow: inherit;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  z-index: 99;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background: #000;

  .wrapper {
    height: 0;
    padding-bottom: 100%;
    width: 100%;

    .gallary-img {
      width: 100%;
    }

    .swiper-pagination {
      color: #fff;
      bottom: -1rem;
    }
  }
}
</style>


