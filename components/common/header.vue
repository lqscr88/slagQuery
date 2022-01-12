<template>
	<view>

		<!-- 顶部导航栏 -->
		<view class="top-navbar">
			<view class="wrap">
				<!-- 左侧手机操作系统链接 -->
				<view class="links os-links">
					<block v-for="(item, index) in osLinks" :key="index">
						<a class="link" :href="item.url" target="_blank">{{item.name}}</a>
						<text v-if="index < osLinks.length - 1" class="separator">|</text>
					</block>
				</view>
				<!-- 右侧用户相关链接 -->
				<view class="links user-links">
					<block>
						<view class="link">登录</view>
						<text class="separator">|</text>
						<view class="link">注册</view>
					</block>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import logo from '../../components/common/logo.vue';
	import userNavs from '../../components/user/common/top-navs.vue';
	import headerConfig from '../../common/config/common/header.config.js';

	export default {
		components: {
			logo,
			userNavs
		},
		props: {
			searchKeyword: {
				type: String,
				default: ''
			}
		},
		data() {
			return {
				osLinks: headerConfig.osLinks,
				brands: [],
				brandIndex: -1,
				showGoodsList: false,
				searchFocus: false,
				hotGoodsList: [],
				promptKeywords: [],
				keyword: this.searchKeyword,
				keywordIndex: -1,
				hiddenAnnouncement: true
			}
		},
		watch: {
			keywordIndex(index) {
				const keyword = this.promptKeywords[index];
				if (keyword) this.keyword = keyword;
			}
		},
		methods: {
		}
	}
</script>

<style lang="scss">
	.top-navbar {
		width: 100%;
		position: relative;
		height: 40px;
		font-size: 12px;
		background-color: $text-color;

		.wrap {
			width: $page-width;
			margin: 0 auto;
			@extend %flex-align-center;
			justify-content: space-between;

			.links {
				height: 40px;
				line-height: 40px;
				@extend %flex-align-center;

				.link {
					color: #b0b0b0;
					cursor: pointer;
					line-height: 40px;

					&:hover {
						color: #FFFFFF;
					}
				}

				.separator {
					margin: 0 .4rem;
					color: #424242;
					line-height: 40px;
				}
			}
		}
	}

	.header-main {
		position: relative;
		height: 100px;

		.container {
			//width: $page-width;
			margin: 0 auto;
			@extend %flex-align-center;

			.header-left {
				width: 234px;
				@extend %flex-align-center;
				justify-content: space-between;

				.all-link {
					color: #333333;
					font-size: 16px;
					cursor: pointer;
					margin-right: 10px;

					&:hover {
						color: $color-primary;
					}
				}
			}

			.header-brands {
				height: 100px;
				padding-left: 10px;
				@extend %flex-align-center;

				.nav-item {
					margin: 0 15px;
					cursor: pointer;
					height: 100px;
					line-height: 100px;

					&:hover {
						color: $color-primary;
					}
				}
			}

			.header-search {
				margin-left: auto;
				position: relative;

				.search-box {
					@extend %flex-align-center;
					border: 1px solid $border-color;
					width: 296px;
					height: 50px;
					transition: all .2s;

					&:hover {
						border: 1px solid #b0b0b0;

						.search-btn {
							border-left: 1px solid #b0b0b0;
						}
					}

					&.active {
						border: 1px solid $color-primary;
					}

					.input-container {
						position: relative;

						.search-input {
							width: 223px;
							height: 48px;
							padding: 0 10px;
							line-height: 48px;
						}

						.hot-goodsList {
							position: absolute;
							top: 16px;
							right: 10px;
							@extend %flex-align-center;

							.item {
								display: block;
								max-width: 85px;
								margin-left: 5px;
								padding: 0 5px;
								font-size: 12px;
								background: #eee;
								color: #757575;
								transition: all .2s;
								cursor: pointer;

								&:hover {
									color: #FFFFFF;
									background-color: $color-primary;
								}
							}
						}
					}

					.search-btn {
						border-left: 1px solid $border-color;
						@extend %flex-align-center;
						justify-content: center;
						width: 52px;
						height: 50px;
						color: #616161;
						cursor: pointer;
						transition: all .2s;

						.icon {
							font-size: 20px;
							font-weight: bold;
						}

						&:hover {
							color: #FFFFFF;
							background-color: $color-primary;
							border: 1px solid $color-primary;
							margin-right: -1px;
						}

						&.active {
							border-left: 1px solid $color-primary;
						}
					}
				}

				.keyword-list {
					z-index: 6;
					position: absolute;
					left: 0;
					width: 243px;
					border: 1px solid $color-primary;
					border-top: none;
					background-color: #FFFFFF;

					.item {
						max-width: 220px;
						font-size: 12px;
						padding: 6px 15px;
						cursor: pointer;

						&:hover {
							background-color: #fafafa;
						}

						&.active {
							background-color: #fafafa;
						}
					}
				}
			}
		}

		.goods-panel {
			background-color: #FFFFFF;
			z-index: 5;
			position: absolute;
			top: 100%;
			left: 0;
			right: 0;
			height: 0;
			overflow: hidden;
			transition: box-shadow .2s, height .3s ease-in;

			&.active {
				height: 229px;
				border-top: 1px solid $border-color;
				box-shadow: 0 3px 4px rgba(0, 0, 0, .18);
			}

			.goods-container {
				width: $page-width;
				margin: 0 auto;
				@extend %flex-align-center;

				.goods {
					text-align: center;
					cursor: pointer;
					font-size: 12px;
					padding: 35px 12px 25px;

					&:first-child {
						margin-left: 50px;
					}

					.thumb {
						width: 160px;
						height: 110px;
						margin-bottom: 15px;
					}

					.name {
						color: #333;
						line-height: 20px;
						max-width: 200px;
					}

					.price {
						color: $color-primary;
						line-height: 20px;
					}
				}

				.separator {
					height: 100px;
					border-right: 1px solid $border-color;
					margin-top: -50px;
				}
			}
		}
	}
</style>
