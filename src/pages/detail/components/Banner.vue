<template>
  <div>
  <div class="banner" @click="handleGallary">
    <img class="banner-img" :src="bannerImg" alt="">
    <div class="banner-info">
      <div class="banner-title">{{ sightName }}</div>
      <div class="banner-number"><i class="iconfont banner-icon">&#xe61b;</i>{{ gallaryImgs.length }}</div>
    </div>
  </div>
  <fade>
    <common-gallary 
      :imgs="gallaryImgs"
      v-show="showGallary"
      @close="gallaryClose"  
    ></common-gallary>
  </fade>
  </div>

</template>

<script>
import commonGallary from "../../../common/gallary/Gallary";
import fade from '../../../common/fade/fade'
export default {
  name: "detailBanner",
  components: {
    commonGallary,
    fade
  },
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data() {
    return {
      showGallary: false
    };
  },
  methods: {
    handleGallary() {
      this.showGallary = true;
    },
    gallaryClose() {
      this.showGallary = false;
    }
  }
};
</script>

<style lang="stylus" scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;

  .banner-img {
    width: 100%;
  }

  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 0.6rem;
    color: #fff;
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

    .banner-title {
      flex: 1;
      font-size: 0.32rem;
      padding: 0 0.2rem;
    }

    .banner-number {
      padding: 0 0.4rem;
      height: 0.32rem;
      line-height: 0.32rem;
      margin-top: 0.14rem;
      border-radius: 0.2rem;
      background: rgba(0, 0, 0, 0.8);
      font-size: 0.24rem;

      .banner-icon {
        font-size: 0.24rem;
      }
    }
  }
}
</style>


