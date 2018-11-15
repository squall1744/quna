<template>
  <div>
    <div class="recommend-title" v-if="showSwiper">热销推荐</div>
    <ul>
      <router-link
        tag="li" 
        class="item border-bottom" 
        v-for="item in recommendList" 
        :key="item.id"
        :to="`/detail/${item.id}`"
      >
        <img class="item-img" :src="item.imgUrl" alt="">
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc">{{ item.desc }}</p>
          <div class="item-button">查看详情</div>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: "recommend",
  props: {
    recommendList: Array
  },
  computed: {
    showSwiper() {
      return this.recommendList.length;
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '../../../assets/styles/mixins.styl';

.recommend-title {
  margin-top: 0.2rem;
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}

.item {
  overflow: hidden;
  display: flex;
  height: 1.9rem;

  .item-img {
    width: 1.7rem;
    height: 1.7rem;
    padding: 0.1rem;
  }

  .item-info {
    flex: 1;
    padding: 0.1rem;
    min-width: 0;

    .item-title {
      line-height: 0.54rem;
      font-size: 0.32rem;
    }

    .item-desc {
      ellipse();
      line-height: 0.4rem;
      color: #eee;
    }

    .item-button {
      background: #ff9300;
      width: 1.2rem;
      padding: 0.1rem;
      border-radius: 0.06rem;
      line-height: 0.2rem;
      margin-top: 0.16rem;
      color: #fff;
    }
  }
}
</style>

