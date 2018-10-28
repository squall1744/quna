<template>
  <div class="wrapper">
  <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
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
    name: 'carrousel',
    data() {
      return {
        // NotNextTick is a component's own property, and if notNextTick is set to true, the component will not instantiate the swiper through NextTick, which means you can get the swiper object the first time (if you need to use the get swiper object to do what Things, then this property must be true)
        // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
        notNextTick: true,
        swiperOption: {
          // swiper options 所有的配置同swiper官方api配置
          autoplay: 1000,
          autoplayDisableOnInteraction: false,
          grabCursor: true,
          setWrapperSize: true,
          pagination: '.swiper-pagination',
          loop: true,
          paginationClickable: true,
          mousewheelControl: true,
          observeParents: true,
          // if you need use plugins in the swiper, you can config in here like this
          // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
        },
        swiperList: [{
          id: 0,
          imgUrl: "http://img1.qunarzz.com/qs/1810/e6/4b890f982670ae02.jpg" 
        },
        {
          id: 1,
          imgUrl: "http://img1.qunarzz.com/qs/1810/db/ab9e1204b6144902.jpg" 
        },
        {
          id: 2,
          imgUrl: "http://img1.qunarzz.com/qs/1809/be/b9098e1abc8a1002.jpg"
        },
        {
          id: 3,
          imgUrl: "http://img1.qunarzz.com/qs/1809/64/62160a38d119c202.jpg" 
        },
        {
          id: 4,
          imgUrl: "http://img1.qunarzz.com/qs/1810/45/ac3ff199b79c5902.jpg" 
        },
        {
          id: 5,
          imgUrl: "http://img1.qunarzz.com/qs/1810/db/ab9e1204b6144902.jpg"
        }]
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background #fff
  .wrapper
    overflow hidden
    width 100%
    height 0
    padding-bottom 31.25%
    .swiper-img
      width 100%

</style>


