<template>
	<view class="container999" @touchstart="refreshStart" @touchmove="refreshMove" @touchend="refreshEnd">
		<!-- 刷新组件需搭配scroll-view使用，并在pages.json中添加 "disableScroll":true-->
		<refresh ref="refresh" @isRefresh='isRefresh'></refresh>
		<view class='nav'>
			<!-- #ifdef H5 -->
			<view style="height: 44px;width: 100%;">边距盒子</view>
			<!-- #endif -->
			<!-- 搜索 -->
			<view class='searchInput999'>
				<view class='searchBox999'>
					<image src='/static/icon-search.png' class='search999'></image>
				</view>
				<input class='input999' placeholder="输入关键词"></input>
			</view>
			<!-- 搜索框下占位盒子，原是swiper选择列表-->
			<view style="height: 44px;width: 100%;"></view>
		</view>
		<view>
			<!-- 搜索框下占位盒子，原是swiper选择列表-->
			<view style="height: 88px;width: 100%;"></view>
			<!--社交宫格宫格-->
			<view class="warp" style="text-align: center;">
				<uni-card is-full :is-shadow="false">
					<text class="uni-h6">渣男渣女查询器</text>
				</uni-card>
				<uni-section title="社交软件" type="line" padding>
					<uni-grid :column="4" :highlight="true" @change="change">
						<uni-grid-item v-for="(item, index) in 6" :index="index" :key="index">
							<view class="grid-item-box" style="background-color: #fff;">
								<uni-icons type="image" :size="30" color="#777" />
								<text class="text">文本信息</text>
							</view>
						</uni-grid-item>
					</uni-grid>
				</uni-section>
			</view>
      <!--第二宫格-->
      <!-- 搜索框下占位盒子，原是swiper选择列表-->
      <view style="width: 100%;"></view>
      <!--社交宫格宫格-->
      <view class="warp" style="text-align: center;">
        <uni-section title="游戏" type="line" padding>
          <uni-grid :column="4" :highlight="true" @change="change">
            <uni-grid-item v-for="(item, index) in 6" :index="index" :key="index">
              <view class="grid-item-box" style="background-color: #fff;">
                <uni-icons type="image" :size="30" color="#777" />
                <text class="text">文本信息</text>
              </view>
            </uni-grid-item>
          </uni-grid>
        </uni-section>
      </view>

      <!--第三宫格-->
      <!-- 搜索框下占位盒子，原是swiper选择列表-->
      <view style="width: 100%;"></view>
      <!--社交宫格宫格-->
      <view class="warp" style="text-align: center;margin-bottom: 50px">
        <uni-section title="其他" type="line" padding>
          <uni-grid :column="4" :highlight="true" @change="change">
            <uni-grid-item v-for="(item, index) in 6" :index="index" :key="index">
              <view class="grid-item-box" style="background-color: #fff;">
                <uni-icons type="image" :size="30" color="#777" />
                <text class="text">文本信息</text>
              </view>
            </uni-grid-item>
          </uni-grid>
        </uni-section>
      </view>

			<!-- 内容结束-->

		</view>
		<tabBar4 :currentPage="currentPage"></tabBar4>
	</view>
</template>

<script>
	const util = require('../../util/util.js');
	import refresh from '../../components/refresh.vue';
	import navTab from '../../components/navTab.vue';
	import tabBar4 from '../../components/tabBar4.vue';
	import uni_card from '../../components/uni-card/uni-card.vue';
	import uni_grid from '../../components/uni-grid/uni-grid.vue';
	import uni_grid_item from '../../components/uni-grid-item/uni-grid-item.vue';
	import uni_section from '../../components/uni-section/uni-section.vue';
	import uni_icons from '../../uni_modules/uni-icons/components/uni-icons/uni-icons';
	export default {
		components: {
			refresh,
			navTab,
			tabBar4,
			uni_card,
			uni_grid,
			uni_grid_item,
			uni_section,
			uni_icons
		},
		data() {
			return {
				currentPage: 'index'
			};
		},
		onLoad(e) {

		},
		onShow() {},
		onHide() {},
		methods: {
			// 刷新touch监听
			refreshStart(e) {
				this.$refs.refresh.refreshStart(e);
			},
			refreshMove(e) {
				this.$refs.refresh.refreshMove(e);
			},
			refreshEnd(e) {
				this.$refs.refresh.refreshEnd(e);
			},
			isRefresh() {
				setTimeout(() => {
					uni.showToast({
						icon: 'success',
						title: '刷新成功'
					})
					this.$refs.refresh.endAfter() //刷新结束调用
				}, 1000)
			}
		}
	};
</script>

<style lang="scss">
	.container999 {
		width: 100vw;
		font-size: 28upx;
		min-height: 100vh;
		overflow: hidden;
		color: #6B8082;
		position: relative;
		background-color: #f6f6f6;
	}

	.content {
		width: 100%;
	}

	.card {
		width: 90%;
		height: 368upx;
		background-color: white;
		margin: 0 auto 42upx auto;
		background: #FFFFFF;
		box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.10);
		border-radius: 5px;
		position: relative;
	}

	.noCard {
		width: 90%;
		height: 200upx;
		margin: auto;
		background-color: white;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #999999;
		box-shadow: 0 0 10upx 0 rgba(0, 0, 0, 0.10);
		border-radius: 10upx;
	}


	.nav {
		position: fixed;
		left: 0;
		top: 0;
		color: white;
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		font-size: 24upx;
		background-color: #50B7EA;
		z-index: 996;
	}

	.searchInput999 {
		width: 90%;
		margin: 0 auto;
		background: white;
		border-radius: 30upx;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 56upx;
	}

	.search999 {
		width: 32upx;
		height: 32upx;
	}

	.searchBox999 {
		width: 56upx;
		height: 56upx;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.input999 {
		color: #999;
		width: 80%;
	}
	/* 宫格 */
	.image {
			width: 50rpx;
			height: 50rpx;
		}
	
		.text {
			font-size: 26rpx;
			margin-top: 10rpx;
		}
	
		.example-body {
			/* #ifndef APP-NVUE */
			// display: block;
			/* #endif */
		}
	
		.grid-dynamic-box {
			margin-bottom: 15px;
		}
	
		.grid-item-box {
			flex: 1;
			// position: relative;
			/* #ifndef APP-NVUE */
			display: flex;
			/* #endif */
			flex-direction: column;
			align-items: center;
			justify-content: center;
			padding: 15px 0;
		}
	
		.grid-item-box-row {
			flex: 1;
			// position: relative;
			/* #ifndef APP-NVUE */
			display: flex;
			/* #endif */
			flex-direction: row;
			align-items: center;
			justify-content: center;
			padding: 15px 0;
		}
	
		.grid-dot {
			position: absolute;
			top: 5px;
			right: 15px;
		}
	
		.swiper {
			height: 420px;
		}
	
		/* #ifdef H5 */
		@media screen and (min-width: 768px) and (max-width: 1425px) {
			.swiper {
				height: 630px;
			}
		}
	
		@media screen and (min-width: 1425px) {
			.swiper {
				height: 830px;
			}
		}
	
		/* #endif */
</style>
