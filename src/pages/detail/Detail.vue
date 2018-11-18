<template>
<div>
  <detail-banner></detail-banner>
  <detail-header></detail-header>  
  <div class="content">
    <detail-List :list="list"></detail-List>
  </div>
</div>
</template>

<script>
import detailBanner from "./components/Banner";
import detailHeader from './components/Header'
import detailList from './components/List'
export default {
  name: "detail",
  components: {
    detailBanner,
    detailHeader,
    detailList
  },
  data() {
    return {
      list: [{
        title: '成人票',
        children: [
          {
            title: '成人三馆联票'
          },
          {
            title: '成人五馆联票'
          }
        ]
      },
      {
        title: '学生票' 
      },
      {
        title: '儿童票'
      },
      {
        title: '特惠票'
      }
      ]
    }
  }
};
</script>

<style lang="stylus" scoped>
  .content
    height 50rem
</style>

