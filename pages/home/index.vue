<template>
	<view class="home_page">
		<!-- <text class="iconfont iconvideocamera"></text> -->
		<!-- <uni-badge text="1"></uni-badge> -->
		
		<view class="top">
			<view class="address" @click="chooseAddress">{{address}}ccc</view>
			<view class="search">
				<input type="text" value="" placeholder="请搜索"/>
				<button>搜索</button>
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
				<swiper-item>2</swiper-item>
			</swiper>
		</navigator>
		<!-- 轮播图结束 -->
		
		<!-- 分区 -->
		<view class="area"></view>
		
		
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
	// import {uniSegmentedControl} from "@dcloudio/uni-ui"
	export default {
		components:{
			// 注册组件
			// uniBadge
			homeFollow,
			homeRecommend,
			homeList,
			
			// uniSegmentedControl
			
		},
		data(){
			return {
				
				title: 'Hello',
				swipers:[],
				address:"df",
				
				
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
						console.log('位置名称：' + res.name);
						console.log('详细地址：' + res.address);
						console.log('纬度：' + res.latitude);
						console.log('经度：' + res.longitude);
						
						
					}
				});
			}
		},
		onLoad() {
			
			// this.request({
			// 	url:""
			// })
			// .then(res=>{
			// 	console.log(res)
			// });
			
			
			this.swipers=['https://app-file.beitaichufang.com/img/H5/web/banner/banner20.jpg',
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner21.jpg",
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner22.jpg",
						"https://app-file.beitaichufang.com/img/H5/web/banner/banner23.jpg"
						];
			
			
			// // 1 原生的微信小程序的api
			// wx.request({
			// 	url:"",
			// 	success(res){
			// 		console.log(res);
			// 	}
			// })
			
			// // 2 uni-api
			// uni.request({
			// 	url:""
			// })
			// .then(res=>{
			// 	console.log(res);
			// })
		}
	}
</script>

<style lang="scss">
	.top{
		display: flex;
		margin: 10rpx 20rpx;
		
		.address{
			flex: 1;
			line-height: 60rpx;
		}
		
		.search{
			display: flex;
			flex: 7;
			input{
				border-radius: 15rpx;
				background-color: #d6d5da;
				height: 60rpx;
				flex: 7;
			}
			
			button{
				flex: 1;
				height: 60rpx;
				font-size: 24rpx;
				line-height: 60rpx;
				margin-right: auto;
			}
		}
		
		
	}
	.home_page{
		
		.home_tab{
			
			.home_tab_title{
				position: relative;
				.title_inner{
					width: 60%;
					margin: 0 auto;
				}
				// .iconsearch{
				// 	position: absolute;
				// 	top: 50%;
				// 	transform: translateY(-50%);
				// 	right: 5%;
					
				// }
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

</style>
