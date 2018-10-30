<template>
  <div class="icons">
     <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper" v-if="showSwiper">
       <swiper-slide v-for="(page, key) in pages" :key="key">
        <div v-for="item in page" :key="item.id" class="icon">
          <img :src="item.imgUrl" alt="">
          <p class="content">{{item.desc}}</p>
        </div>
       </swiper-slide>
       <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "icons",
  props: {
    iconList: Array
  },
  data() {
    return {
      notNextTick: true,
      swiperOption: {
        // swiper options 所有的配置同swiper官方api配置
        autoplay: false,
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
    pages() {
      const pages = [];
      this.iconList.map((item, index) => {
        const page = Math.floor(index / 8);
        if (pages[page] === undefined) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    },
    showSwiper() {
      return this.iconList.length;
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '../../../assets/styles/mixins.styl';

.icons >>> .swiper-pagination-bullet-active {
  background: green;
}

.icons {
  display: flex;
  overflow: hidden;
  width: 100%;
  height: 53vw;
  flex-wrap: wrap;

  .icon {
    float: left;
    width: 25%;
    height: 0;
    padding-bottom: 20%;
    font-size: 14px;
    text-align: center;
    margin-top: 0.2rem;

    img {
      width: 1.1rem;
      height: 1.1rem;
    }

    .content {
      ellipse();
    }
  }
}
</style>