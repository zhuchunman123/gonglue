<template>
	<view class="content">

		<!-- 定位   搜索栏 （待完善）-->
		<view class="top">
			<view class="address" @click="chooseAddress">选择</view>
			<view class="search">
				<input class="iconfont iconsearch" type="text" value="" placeholder="搜索" />
				<view class="sousuo">搜索</view>
			</view>

		</view>
		<!-- 职业创作者推荐 -->
		<view style="margin: 10rpx 20rpx;font-size: 16px;color: #333333;">创作者推荐</view>
		<view class="creator">
			<scroll-view scroll-x="true" class="scroll">
				<view class="box" v-for="(item,index) in creators" :key="index">
					<image :src="item.image" mode=""></image>
					<text>{{item.nickname}}</text>
				</view>
			</scroll-view>
		</view>

		<!-- 轮播图开始 -->
		<navigator class='home'>
			<swiper indicator-dots circular autoplay interval=3000>
				<swiper-item v-for="(item,index) in swipers" :key="index">
					<image :src="item"></image>
				</swiper-item>
			</swiper>
		</navigator>
		<!-- 轮播图结束 -->

		<!-- 综合排序、点赞最高、收藏最多，评论最多 -->
		<view class="sort">
			<text @click="zonghe">综合排序</text>
			<text @click="dianzan">点赞最高</text>
			<text @click="shoucang">收藏最多</text>
			<text@click="pinlun">评论最多</text>
		</view>
		
		<view>
			<home-recommend></home-recommend>
		</view>
		
		



	</view>
</template>

<script>
	
	import homeRecommend from '../home/home-recommend/index.vue'
	export default {
		components:{
			homeRecommend
		},
		
		data() {
			return {

				// 职业写手推荐，包含头像及昵称，（其他信息）
				// 示例列表
				creators: [{
						image: "https://img1.baidu.com/it/u=2305185901,8723802&fm=26&fmt=auto&gp=0.jpg",
						nickname: "懒羊羊"
					},
					{
						image: "https://img1.baidu.com/it/u=2305185901,8723802&fm=26&fmt=auto&gp=0.jpg",
						nickname: "懒羊羊"
					},
					{
						image: "https://img1.baidu.com/it/u=2305185901,8723802&fm=26&fmt=auto&gp=0.jpg",
						nickname: "懒羊羊"
					},
					{
						image: "https://img1.baidu.com/it/u=2305185901,8723802&fm=26&fmt=auto&gp=0.jpg",
						nickname: "懒羊羊"
					}
				],
			}
		},
		methods: {

			chooseAddress() {
				uni.chooseLocation({
					success: function(res) {
						// console.log('位置名称：' + res.name);
						console.log('详细地址：' + res.address);
						// console.log('纬度：' + res.latitude);
						// console.log('经度：' + res.longitude);
						this.address = res.address

					}
				});
			},
			zonghe(){
				this.list= this.list1
			},
			dianzan(){
				this.list = this.list2
			},
			shoucang(){
				this.list = this.list3
			},
			pinlun(){
				this.list = this.list4
			}

		},
		onLoad() {
			this.swipers = ['https://app-file.beitaichufang.com/img/H5/web/banner/banner20.jpg',
				"https://app-file.beitaichufang.com/img/H5/web/banner/banner21.jpg",
				"https://app-file.beitaichufang.com/img/H5/web/banner/banner22.jpg",
				"https://app-file.beitaichufang.com/img/H5/web/banner/banner23.jpg"
			];
			this.list = this.list1
		}
	}
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



	.creator {
		padding-top: 5rpx;

		// background-color: #FFFFFF;
		.scroll {
			width: 100%;
			overflow: hidden;
			white-space: nowrap;

			.box {
				display: inline-block;
				width: 200rpx;
				height: 250rpx;
				background: #ffffff;
				margin-right: 20rpx;
				margin-bottom: 10rpx;
				padding-top: 25rpx;
				box-shadow: 5px 10px 5px #888888;
				text-align: center;

				image {
					width: 150rpx;
					height: 150rpx;
					border-radius: 50%;
					margin: 0 auto;
				}

				text {
					background-color: #FFFFFF;
					line-height: 50rpx;

				}
			}

			.box:first-child {
				margin-left: 20rpx;
			}
		}
	}

	.home {
		swiper {
			width: 750rpx;
		}

		image {
			width: 100%;
			height: 100%;
		}
	}

	.sort {
		display: flex;
		margin-top: 20rpx;

		text {
			flex: 1;
			text-align: center;
		}
	}
</style>
