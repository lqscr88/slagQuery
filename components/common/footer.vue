<template>
	<view>

		<!-- 上半部分 -->
		<view class="up-half-wrapper">
			<view class="wrap">
				<!-- 更多服务 -->
				<view class="service-more">
					<!-- 服务链接 -->
					<view class="links">
						<view class="item" v-for="(item, index) in links" :key="index">
							<view class="title">{{item.title}}</view>
							<view class="list">
								<block v-for="(link, linkIndex) in item.list" :key="linkIndex">
									<a class="link" :href="link.linkUrl" target="_blank" @click.stop.prevent="hiddenWechatInfo = false;">{{link.name}}</a>
								</block>
							</view>
						</view>
					</view>
					<!-- 联系我们 -->
					<view class="contact">
						<view class="telphone-number">{{contact.telphoneNumber}}</view>
						<view class="service-range">
							<view class="detail">{{contact.serviceDayRange}} {{contact.serviceTimeRange}}</view>
							<view class="tip">（仅收市话费）</view>
						</view>
						<view class="btn-message" @click="openOnlineService">
							<i class="icon i-message"></i>
							<text class="name">人工客服</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import footerConfig from '../../common/config/common/footer.config.js';

	export default {
		data() {
			return {
				...footerConfig,
				hiddenWechatInfo: true
			}
		},
		methods: {
			closeDialog() {
				this.hiddenWechatInfo = true;
			},
			openOnlineService() {
				window.open('https://support.kefu.mi.com', 'smallwin', 'width=500, height=750, statue=yes');
			}
		}
	}
</script>

<style lang="scss">
	.up-half-wrapper {
		background-color: $bg-color;

		.wrap {
			width: $page-width;
			margin: 0 auto;

			.service-wrap {
				padding: 27px 0;
				border-bottom: 1px solid #e0e0e0;
				@extend %flex-align-center;
				justify-content: space-between;

				.service {
					width: 19.8%;
					height: 25px;
					border-left: 1px solid #e0e0e0;
					@extend %flex-align-center;
					justify-content: center;
					color: #616161;
					transition: color .2s;

					&:first-child {
						border-left: none;
					}

					&:hover {
						color: $color-primary;
					}

					.icon {
						margin-right: 6px;
						font-size: 24px;
					}

					.name {
						font-size: 16px;
					}
				}
			}

			.service-more {
				@extend %flex-align-center;
				justify-content: space-between;

				.links {
					display: flex;

					.item {
						width: 160px;
						text-align: center;

						.title {
							margin: 26px auto;
							line-height: 1.25;
							color: #424242;
						}

						.link {
							margin-bottom: 10px;
							color: #757575;
							font-size: 12px;
							display: block;

							&:hover {
								color: $color-primary;
							}
						}
					}
				}

				.contact {
					width: 242px;
					height: 112px;
					border-left: 1px solid #e0e0e0;
					text-align: center;

					.telphone-number {
						margin-bottom: 5px;
						font-size: 22px;
						line-height: 1;
						color: $color-primary;
					}

					.service-range {
						margin-bottom: 16px;
						font-size: 12px;
						color: #616161;
					}

					.btn-message {
						margin: 0 auto;
						@extend %flex-align-center;
						justify-content: center;
						width: 118px;
						height: 28px;
						border: 1px solid $color-primary;
						cursor: pointer;
						transition: all .4s;

						&:hover {
							background-color: $color-primary;

							.icon {
								color: $bg-color;
							}

							.name {
								color: $bg-color;
							}
						}

						.icon {
							display: inline-block;
							font-size: 16px;
							color: $color-primary;
							margin-right: 2px;
						}

						.name {
							font-size: 12px;
							color: $color-primary;
						}
					}
				}
			}
		}
	}

	.down-half-wrapper {
		background-color: $bg-color-grey;

		.wrap {
			width: $page-width;
			margin: 0 auto;

			.site-info-wrap {
				display: flex;
				padding-top: 30px;

				.logo {
					width: 57px;
					height: 57px;
					margin-right: 10px;
				}

				.site-info {

					.links a {
						color: #757575;
						line-height: 18px;
						font-size: 12px;
						padding: 0 5px;
						border-left: 1px solid #b0b0b0;

						&:first-child {
							padding-left: 0;
							border-left: none;
						}

						&:hover {
							color: $color-primary;
						}
					}

					.info-text {
						color: #b0b0b0;
						line-height: 18px;
						font-size: 12px;
					}

					.info-images {
						display: flex;
						margin-top: 5px;

						.link-image {
							width: 100px;
							height: 28px;
							object-fit: contain;
							margin-bottom: 5px;

							&:first-child {
								margin-left: -8px;
							}
						}
					}
				}
			}

			.slogan {
				margin: 20px 0;
				width: 100%;
				height: 21px;
				object-fit: contain;
			}
		}
	}

	.qrcode {
		width: 680px;
		height: 340px;
	}
</style>
