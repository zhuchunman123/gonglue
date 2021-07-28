<template>

	<view class="all">
		<!-- 定位   搜索栏 （待完善）-->
		<view class="top">
			<view class="address" @click="chooseAddress">{{address}}选择</view>
			<view class="search">
				<input class="iconfont iconsearch" type="text" value="" placeholder="搜索" />
				<view class="sousuo">搜索</view>
			</view>

		</view>


		<!-- 侧边菜单主体 -->
		<view class="main">
			<scroll-view scroll-y class="left_sv">
				<view class="menu_item" v-for="(item, index) in list" :key="index" :class="active_index === index ? 'active' : ''"
				 @click="handle_tab(index)">
					{{ item.name }}
				</view>
			</scroll-view>
			<scroll-view scroll-y class="right_sv">
				<view class="right_content" v-for="(item,index) in array" :key="index">
					<view class="title">{{item.name}}</view>
					<view class="contentList">
						<view class="listItems" v-for="(items,contents) in array[0].content" :key="contents">

							<view class="content">
								<image :src="items.image" mode=""></image>
								<text>{{items.name}}</text>
							</view>
						</view>

					</view>
				</view>
			</scroll-view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				address:"",
				
				active_index: 0,
				list: [{
						name: 'hello'
					},
					{
						name: 'hello1'
					},
					{
						name: 'hello2'
					},
					{
						name: 'hello3'
					}
				],
				site: [{
						name: 'hello',
						content: [{
								name: "广州",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							},
							{
								name: "广州",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							}
						]
					},
					{
						name: 'hello1',
						content: [{
								name: "北京",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							},
							{
								name: "北京",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							}
						]
					},
					{
						name: 'hello2',
						content: [{
								name: "上海",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							},
							{
								name: "上海",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							}
						]
					},
					{
						name: 'hello3',
						content: [{
								name: "深圳",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							},
							{
								name: "深圳",
								image: "https://img0.baidu.com/it/u=3844939064,2416681391&fm=26&fmt=auto&gp=0.jpg"
							}
						]
					},

				],
				array: []
			};
		},

		created() {
			// 初始化数据默认选中第一个
			this.array.push(this.site[0])
		},
		methods: {
			handle_tab(index) {
				this.array = [],
					this.active_index = index,
					this.array.push(this.site[index])
			},
			chooseAddress(){
				uni.chooseLocation({
					success: function (res) {
						// console.log('位置名称：' + res.name);
						console.log('详细地址：' + res.address);
						// console.log('纬度：' + res.latitude);
						// console.log('经度：' + res.longitude);
						this.address = res.address
						
					}
				});
			}
		}
	};
</script>

<style lang="scss" scoped>
	.top {
		display: flex;
		padding: 10rpx 20rpx;
		border-bottom: 1px solid #f0f0f0;

		.address {
			width: 100rpx;
			height: 60rpx;
			line-height: 60rpx;
			text-align: center;
			overflow: hidden;
		}

		.search {
			display: flex;
			width: 100%;
			line-height: 60rpx;

			input {
				border-radius: 50rpx;
				background-color: #e9e8ec;
				height: 60rpx;
				flex: 5;
				padding-left: 20rpx;
				margin-right: 10rpx;

				line-height: 60rpx;
			}

			sousuo {
				height: 60rpx;
				font-size: 24rpx;
				text-align: center;
				background-color: #f4f4f4;
			}
		}
	}

	.main {
		display: flex;
		height: 100vh;

		.left_sv {
			flex: 2;
			font-size: 28rpx;
			font-weight: 400;

			.menu_item {
				height: 80rpx;
				line-height: 80rpx;
				text-align: center;
				color: #333333;
				background-color: #F3F3F3;

			}

			.active {
				height: 80rpx;
				line-height: 80rpx;

				background-color: #E2EDFF;
				color: #2F77F1;
				border-left: 4px solid #2F77F1;
			}
		}

		.right_sv {

			flex: 5;
			background-color: #ffffff;

			.right_content {

				.title {
					background-color: #FFFFFF;
				}

				.contentList {

					.listItems {
						padding: 20rpx;
						background-color: #FFFFFF;

						.content {
							background-color: #FFFFFF;
							margin: 20rpx 0;

							image {
								width: 100%;
								height: 300rpx;
							}

							text {
								background-color: #FFFFFF;
							}
						}
					}
				}
			}
		}
	}
</style>
