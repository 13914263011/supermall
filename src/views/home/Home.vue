<template>
  <div id="home">
    <nav-bar class="nav-bar">
      <div slot="center">购物街</div>
    </nav-bar>
    <swiper :banners="banners"/>
  </div>
</template>

<script>
  import NavBar from '@/components/common/navbar/NavBar';
  import Swiper from './childComps/Swiper';

  import {getHomeMultidata} from '../../network/home';

  export default {
    name: 'Home',
    components: {
      NavBar,
      Swiper,
    },
    data() {
      return {
        banners: [],
        recommends: [],
      };
    },
    created() {
      // 1.请求多个数据
      getHomeMultidata().then(res => {
        console.log(res);
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
  };
</script>

<style scoped>
  #home {
    /*position: relative;*/
    height: 100vh;
  }

  .nav-bar {
    background-color: #ff8198;
    font-weight: 700;
    color: #fff;
    width: 100%;
  }

</style>
