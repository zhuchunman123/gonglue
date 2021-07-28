<!-- 作者：罗双 2021-7-20 完成初稿 -->
<!-- 作者：丁睿 2021-7-21 -->

<template>
	<view class="home_page">
		
		<!-- 定位   搜索栏 （待完善）-->
		<view class="top">
			<view class="address" @click="chooseAddress">{{address}}选择</view>
			<view class="search">
				<input class="iconfont iconsearch" type="text" value="" placeholder="搜索"/>
				<view class="sousuo">搜索</view>
			</view>
			
		</view>
		
		<!-- 轮播图开始 -->
		<navigator class='home' url="../details/details">
			<swiper
			indicator-dots
			circular
			autoplay
			interval=3000
			>
				<swiper-item v-for="(item,index) in swipers" :key="index">
					<image :src="item"></image>
				</swiper-item>
			</swiper>
		</navigator>
		<!-- 轮播图结束 -->
		
		<!-- 分区 -->
		<view class="area_list">
			<navigator class="area_item" v-for="item in areas" :key = "item.id" :url="item.url">
				<view class="area_img"><image :src="item.cover" mode=""></image></view>
				<view class="area_title">{{item.title}}</view>
			</navigator>
		</view>
		
		
		<!-- 分段器，关注、推荐、热榜 -->
		<view class="home_tab">
			<view class="home_tab_title">
				<view class="title_inner">
					<uni-segmented-control 
					:current="current" 
					:values="items.map(v=>v.title)" 
					@clickItem="onClickItem" 
					styleType="text" 
					activeColor="#d4237a"
					></uni-segmented-control>
				</view>
				<!-- <view class="iconfont iconsearch"></view> -->
			</view>
			
			<view class="home_tab_content">
				<view v-if="current === 0">
					<home-follow></home-follow>
				</view>
				<view v-if="current === 1">
					<home-recommend></home-recommend>
					
				</view>
				<view v-if="current === 2">
					<home-list></home-list>
				</view>
			</view>
		</view>

		
		
	</view>
</template>

<script>
	
	// import {uniBadge} from "@dcloudio/uni-ui"
	import homeFollow from "./home-follow"
	import homeRecommend from "./home-recommend"
	import homeList from "./home-list"
	
	// 引入分段器组件
	import {uniSegmentedControl} from "@dcloudio/uni-ui"
	export default {
		components:{
			// 注册组件
			// uniBadge
			homeFollow,
			homeRecommend,
			homeList,
			
			uniSegmentedControl
			
		},
		data(){
			return {
				
				title: 'Hello',
				swipers:[],
				address:"",
				// 分区列表
				areas:[
					{
						cover:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F40125%2F0071.gif_wh300.gif%21%2Fgifto%2Ftrue&refer=http%3A%2F%2Fimg95.699pic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629288120&t=ff9b7266a4adffb3039e07f0c159072a",
						title:"自然探索"
					},
					{
						cover:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F40125%2F0071.gif_wh300.gif%21%2Fgifto%2Ftrue&refer=http%3A%2F%2Fimg95.699pic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629288120&t=ff9b7266a4adffb3039e07f0c159072a",
						title:"人文风土"
					},
					{
						cover:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F40125%2F0071.gif_wh300.gif%21%2Fgifto%2Ftrue&refer=http%3A%2F%2Fimg95.699pic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629288120&t=ff9b7266a4adffb3039e07f0c159072a",
						title:"职业攻略",
						url:"/pages/strategy/index"
					},
					{
						cover:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F40125%2F0071.gif_wh300.gif%21%2Fgifto%2Ftrue&refer=http%3A%2F%2Fimg95.699pic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629288120&t=ff9b7266a4adffb3039e07f0c159072a",
						title:"城市足迹"
					},
					{
						cover:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F40125%2F0071.gif_wh300.gif%21%2Fgifto%2Ftrue&refer=http%3A%2F%2Fimg95.699pic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629288120&t=ff9b7266a4adffb3039e07f0c159072a",
						title:"乡土乐趣"
					}
				],
				
				items:[
					{title:"关注"},
					{title:"推荐"},
					{title:"热榜"},
				],
				current:1
			};
		},
		methods:{
			onClickItem(e){
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
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
		},
		onLoad() {
			this.swipers=['https://app-file.beitaichufang.com/img/H5/web/banner/banner20.jpg',
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner21.jpg",
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner22.jpg",
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner23.jpg"
						];
		}
	}
</script>

<style lang="scss">
	.top{
		display: flex;
		padding: 10rpx 20rpx;
		border-bottom: 1px solid #f0f0f0;
		.address{
			width: 100rpx;
			height: 60rpx;
			line-height: 60rpx;
			text-align: center;
			overflow: hidden;
		}
		
		.search{
			display: flex;
			width: 100%;
			line-height: 60rpx;
			input{
				border-radius: 50rpx;
				background-color: #e9e8ec;
				height: 60rpx;
				flex: 5;
				padding-left: 20rpx;
				margin-right: 10rpx;
				
				line-height: 60rpx;
			}
			
			sousuo{
				height: 60rpx;
				font-size: 24rpx;
				text-align: center;
				background-color: #f4f4f4;
			}
		}
	}
	.home_page{
		background-color: #f1f1f1;
		.home_tab{
			background-color: #FFFFFF;
			.home_tab_title{
				position: relative;
				.title_inner{
					width: 100%;
					margin: 0 auto;
				}
				
			}
		}
		.home{
			swiper{
				width: 750rpx;
			}
			image{
				width: 100%;
				height: 100%;
			}
		}
	}
	.area_list{
		background-color: #FFFFFF;
		display: flex;
		padding: 10rpx 20rpx;
		margin-bottom: 10rpx;
		.area_item{
			background-color: #FFFFFF;
			flex: 1;
			height: 180rpx;
			flex-direction: column;
			flex: 1;
			.area_img{
				height: 120rpx;
				margin: 10rpx 5rpx;
				border-radius: 50%;
				overflow: hidden;
				image{
					width: 100%;
					height: 100%;
					
				}
			}
			.area_title{
				background-color: #FFFFFF;
				height: 30rpx;
				line-height: 40rpx;
				font-size: 24rpx;
				font-weight: bold;
				text-align: center;
			}
		}
	}
</style>
