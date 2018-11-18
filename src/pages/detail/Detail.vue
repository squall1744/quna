<template>
<div>
    <detail-banner
      :sightName="sightName"
      :bannerImg="bannerImg"
      :gallaryImgs="gallaryImgs"
    ></detail-banner>
    <keep-alive>
      <detail-header></detail-header>  
    </keep-alive>
    <div class="content">
      <detail-List :list="categoryList"></detail-List>
    </div>
</div>
</template>

<script>
import detailBanner from "./components/Banner";
import detailHeader from './components/Header'
import detailList from './components/List'
import axios from 'axios'
export default {
  name: "detail",
  components: {
    detailBanner,
    detailHeader,
    detailList
  },
  data() {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      categoryList: []
    }
  },
  methods: {
    getDetailInfo() {
      axios.get('/mock/detail.json', {
        params: {
          id: this.$route.params.id
        }
        }).then(res => this.getDetailInfoSucc(res))
    },
    getDetailInfoSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        this.sightName = res.data.sightName
        this.bannerImg = res.data.bannerImg
        this.gallaryImgs = res.data.gallaryImgs
        this.categoryList = res.data.categoryList
      }
    }
  },
  created() {
    this.getDetailInfo()
  }
};
</script>

<style lang="stylus" scoped>
  .content
    height 50rem
</style>

