<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <FeatureView></FeatureView>
    <tab-control class="tab-control" :titles="['流行', '新款', '精选']"></tab-control>
    <ul>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
      <li><h2>111</h2></li>
    </ul>
  </div>
</template>

<script>
  import HomeSwiper from "./childComps/HomeSwiper";
  import RecommendView from "./childComps/RecommendView";
  import FeatureView from "./childComps/FeatureView";

  import NavBar from "components/common/navbar/NavBar";
  import TabControl from "components/content/tabContorl/TabControl";

  import {getHomeMultiData} from "network/home";

  export default {
    name: "Home",
    components: {
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl
    },
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    // 在组件创建之前进行网络请求，将数据传入组件中
    created() {
      getHomeMultiData().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
  #home {
    padding-top: 44px;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #ffffff;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 9;
  }

  .tab-control {
    /*sticky属性的作用：当top没有达到设定值时，可以跟随页面同时滚动。当达到top值之后，会默认将sticky转变为fixed，停留在页面的位置上*/
    position: sticky;
    top: 44px;
    background-color: #fff;
  }
</style>
