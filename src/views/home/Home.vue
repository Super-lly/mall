<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners" />
  </div>
</template>

<script>
import HomeSwiper from "./childComps/HomeSwiper";
import NavBar from "components/common/navbar/NavBar";
import {getHomeMultidata} from "network/home";
export default {
  name: "Home",
  components: {
    HomeSwiper,
    NavBar,
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
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
</style>