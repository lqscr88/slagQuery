<template>
  <view>

    <!-- 顶部横幅 -->
    <banner v-if="topBanner" :banner="topBanner" top></banner>

    <!-- 页首 -->
    <zw_header></zw_header>

    <!-- 页脚 -->
    <zw_footer></zw_footer>

  </view>
</template>

<script>
import banner from '../../components/home/banner.vue';
import zw_header from '../../components/common/header.vue';
import zw_footer from '../../components/common/footer.vue';

export default {
  components: {
    banner,
    zw_header,
    zw_footer
  },
  data() {
    return {
      topBanner: null,
      scrollTop: 0,
      adverts: [],
      brickCategories: []
    }
  },
  onLoad() {
    this.findTopBanner();
    this.findAdverts();
    this.findBrickCategories();
  },
  onShow() {
    // 监听滚动
    window.addEventListener('scroll', this.onScroll);
  },
  onHide() {
    // 取消滚动监听
    window.removeEventListener('scroll', this.onScroll);
  },
  methods: {
    /**
     * 解决onPageScroll有时不触发的问题
     */
    onScroll() {
      this.scrollTop = window.scrollY;
    },
    findTopBanner() {

    },
    findAdverts() {

    },
    findBrickCategories() {

    }
  }
}
</script>