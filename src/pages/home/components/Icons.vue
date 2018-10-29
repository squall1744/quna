<template>
  <div class="icons">
     <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
       <swiper-slide v-for="(page, key) in pages" :key="key">
        <div v-for="item in page" :key="item.id" class="icon">
          <img :src="item.imgUrl" alt="">
          <p class="content">{{item.content}}</p>
        </div>
       </swiper-slide>
       <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "icons",
  data() {
    return {
      iconList: [
        {
          id: 0,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
          content: "景点门票"
        },
        {
          id: 1,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
          content: "北京必游"
        },
        {
          id: 2,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png",
          content: "一日游"
        },
        {
          id: 3,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png",
          content: "文化古迹"
        },
        {
          id: 4,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png",
          content: "动植物园"
        },
        {
          id: 5,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          content: "故宫"
        },
        {
          id: 6,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png",
          content: "野生动物园"
        },
        {
          id: 7,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png",
          content: "泡温泉"
        },
        {
          id: 8,
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png",
          content: "泡温泉"
        }
      ],
      notNextTick: true,
      swiperOption: {
        // swiper options 所有的配置同swiper官方api配置
        grabCursor: true,
        setWrapperSize: true,
        pagination: ".swiper-pagination",
        loop: true,
        paginationClickable: true,
        mousewheelControl: true,
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


