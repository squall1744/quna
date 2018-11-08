<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconList="iconList"></home-icons>
    <home-recommend :recommendList="recommendList"></home-recommend>
    <home-weekend :weekendList="weekendList"></home-weekend>
  </div>

</template>

<script>
import homeHeader from "./components/Header";
import homeSwiper from "./components/Swiper";
import homeIcons from "./components/Icons";
import homeRecommend from "./components/Recommend";
import homeWeekend from "./components/Weekend";
import axios from "axios";
import { mapState } from "vuex";
export default {
  name: "home",
  components: {
    homeHeader,
    homeSwiper,
    homeIcons,
    homeRecommend,
    homeWeekend
  },
  data() {
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: [],
      lastCity: ""
    };
  },
  methods: {
    getHomeInfo() {
      axios
        .get(`/mock/index.json?city=${this.city}`)
        .then(this.getHomeInfoSucc);
    },
    getHomeInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        this.swiperList = res.data.swiperList;
        this.iconList = res.data.iconList;
        this.recommendList = res.data.recommendList;
        this.weekendList = res.data.weekendList;
      }
    }
  },
  computed: {
    ...mapState({
      city: "city"
    })
  },
  mounted() {
    this.getHomeInfo();
    this.lastCity = this.city;
  },
  activated() {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city;
      this.getHomeInfo();
    }
  }
};
</script>

<style lang="stylus" scoped>
</style>

