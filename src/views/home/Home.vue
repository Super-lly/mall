<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners" />
    <recommend-view :recommends="recommends"/>
    <feature-view/>
  </div>
</template>

<script>
import HomeSwiper from "./childComps/HomeSwiper";
import NavBar from "components/common/navbar/NavBar";
import {getHomeMultidata} from "network/home";
import RecommendView from "./childComps/RecommendView.vue"
import FeatureView from "./childComps/FeatureView.vue"
export default {
  name: "Home",
  components: {
    HomeSwiper,
    NavBar,
    RecommendView,
    FeatureView
  },
  data() {
    return {
      banners: [],
      recommends: [],
    };
  },
  created() {
    getHomeMultidata().then((res) => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  },
};
</script>

<style scoped>
#home{
  padding-top: 44px;
}
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
  /* position: fixed;
  top: 0;
  left: 0;
  right: 0; */
}
</style>