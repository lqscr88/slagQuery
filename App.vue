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
        // this.$router.replace('/m_index');
      } else {
        console.log("pc端")
        // this.$router.replace('/pc_index');
      }
    },
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
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
