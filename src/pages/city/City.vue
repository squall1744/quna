<template>
<div>
  <city-header></city-header>
  <city-search></city-search>
  <city-list 
    :cities="cities"
    :hotCities="hotCities"
    :letter="xxx"
  ></city-list>

  <city-alpabet 
    :cities="cities"
    @change="text"
  ></city-alpabet>
</div>
</template>

<script>
import cityHeader from "./components/Header";
import citySearch from "./components/Search";
import cityList from "./components/List";
import cityAlpabet from "./components/Alphabet";
import axios from "axios";
export default {
  name: "city",
  components: {
    cityHeader,
    citySearch,
    cityList,
    cityAlpabet
  },
  mounted() {
    this.getCityInfo();
  },
  data() {
    return {
      cities: {},
      hotCities: [],
      xxx: ""
    };
  },
  methods: {
    getCityInfo() {
      axios.get("/mock/city.json").then(this.getCityInfoSucc);
    },
    getCityInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        const data = res.data;
        this.cities = data.cities;
        this.hotCities = data.hotCities;
      }
    },
    text(a) {
      this.xxx = a;
    }
  }
};
</script>

<style lang="stylus" scoped>
</style>

