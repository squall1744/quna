<template>
<div>
  <div class="search">
    <input type="text" class="search-input" placeholder="输入城市名或拼音" v-model="keyWords">
  </div> 
  <div class="search-content" 
    ref="search"
    v-show="keyWords"   
  >
    <ul>
      <li class="search-item border-bottom" v-for="item in list" 
        :key="item.id"
        @click="handleSearchCity(item.name)"
      >{{ item.name }}</li>
      <li v-show="hasNoData">当前没有匹配项</li>
    </ul>
  </div>
</div>
</template>

<script>
import Bscroll from "better-scroll";
export default {
  name: "citySearch",
  props: {
    cities: Object
  },
  data() {
    return {
      keyWords: "",
      list: [],
      timer: null
    };
  },
  computed: {
    hasNoData() {
      return !this.list.length;
    }
  },
  watch: {
    keyWords() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      if (!this.keyWords) {
        this.list = [];
        return null;
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.cities) {
          this.cities[i].map(value => {
            if (
              value.spell.indexOf(this.keyWords) > -1 ||
              value.name.indexOf(this.keyWords) > -1
            ) {
              result.push(value);
            }
          });
        }
        this.list = result;
      }, 100);
    }
  },
  methods: {
    handleSearchCity(city) {
      this.$store.dispatch("changeCity", city);
      this.$router.push("/");
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.search);
  }
};
</script>

<style lang="stylus" scoped>
@import '../../../assets/styles/varibles.styl';

.search {
  height: 0.72rem;
  padding: 0 0.1rem;
  background: $bgColor;

  .search-input {
    width: 100%;
    height: 0.62rem;
    padding: 0 0.1rem;
    line-height: 0.62rem;
    text-align: center;
    border-radius: 0.06rem;
    color: #666;
  }
}

.search-content {
  z-index: 1;
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
  background: #eee;

  .search-item {
    line-height: 0.62rem;
    padding-left: 0.2rem;
    color: #666;
    background: #fff;
  }
}
</style>


