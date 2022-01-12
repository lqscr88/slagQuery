<script>
	export default {
	  methods:{
      _isMobile() {
        let flag = navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
        return flag;
      }
    },
    mounted() {
      if (this._isMobile()) {
        console.log("手机端")
        // this.$router.push('pages/index/index')
		uni.navigateTo({
		    url: 'pages/index/index'
		});
      } else {
        console.log("pc端")
        // this.$router.push('pages/pc/index')
		uni.navigateTo({
		    url: 'pages/pc/index'
		});
      }
    }
	}
</script>

<style>
	/*每个页面公共css */
	::-webkit-scrollbar {
	  width: 0;
	  height: 0;
	  color: transparent;
	}
</style>
