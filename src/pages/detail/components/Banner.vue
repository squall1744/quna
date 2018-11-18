<template>
  <div>
  <div class="banner" @click="handleGallary">
    <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_600x330_df3d1e0a.jpg" alt="">
    <div class="banner-info">
      <div class="banner-title">三亚千古情景区</div>
      <div class="banner-number"><i class="iconfont banner-icon">&#xe61b;</i>39</div>
    </div>
  </div>
  <common-gallary 
    :imgs="imgs"
    v-show="showGallary"
    @close="gallaryClose"  
  ></common-gallary>
  </div>

</template>

<script>
import commonGallary from "../../../common/gallary/Gallary";
export default {
  name: "detailBanner",
  components: {
    commonGallary
  },
  data() {
    return {
      imgs: [
        "http://img1.qunarzz.com/sight/p0/1411/12/61b9be8c7bd5ff48a86add2eddd93517.water.jpg_r_800x800_dc03df8f.jpg",
        "http://img1.qunarzz.com/sight/p0/1411/12/61b9be8c7bd5ff48a86add2eddd93517.water.jpg_r_800x800_dc03df8f.jpg"
      ],
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


