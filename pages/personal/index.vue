<template>
	
	<view>
		<!-- 背景 -->
		<view class="back">
			<image src="https://ss0.baidu.com/94o3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/cb8065380cd791230f4870a5ac345982b3b780b3.jpg" mode=""></image>
		</view>
		
		<!-- 个人信息 -->
		<view class="describe">
			
			<!-- 头像 -->
			<image class="des_img" src="https://ss0.baidu.com/94o3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/cb8065380cd791230f4870a5ac345982b3b780b3.jpg" mode=""></image>
			
			<!-- 昵称  跳转到个人资料编辑页面 -->
			<navigator class="info" url="data_edit">
				<text>我是一个粉刷匠</text>
				<image src="../../static/icon/写字版.png" mode=""></image>
			</navigator>
			
			<!-- 关注、粉丝、获赞管理 -->
			<view class="manage">
				<text>关注{{guanzhu}} | 粉丝{{fensi}} | 获赞{{huozan}}</text>
			</view>
			
			<!-- 本人（进入创作）   他人主页（关注按钮） -->
			
			<!-- 职业认证标识    v-show -->
			<view class="medal">职业玩家认证</view>
			
			<!-- 简介 -->
			<view class="introduction">
				简介，即简明扼要的介绍。是当事人全面而简洁地介绍情况的一种书面表达方式，它是应用写作学研究的一种日常应用文体。
			</view>
			
			<!-- 发布    草稿 -->
			<!-- 分段器，关注、推荐、热榜 -->
			<view class="home_tab">
				<view class="home_tab_title">
					<view class="title_inner">
						<uni-segmented-control 
						:current="current" 
						:values="items.map(v=>v.title)" 
						@clickItem="onClickItem" 
						styleType="text" 
						activeColor="#d48a8b"
						></uni-segmented-control>
					</view>
				</view>
				
				<view class="home_tab_content">
					<view v-if="current === 0">
						<post></post>
					</view>
					<view v-if="current === 1">
						<draft></draft>
					</view>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	import post from './post.vue'
	import draft from './draft.vue'
	
	import {uniSegmentedControl} from "@dcloudio/uni-ui"
	export default {
		components:{
			post,
			draft,
			uniSegmentedControl
		},
		data(){
			return {
				guanzhu:12,
				fensi:12,
				huozan:12,
				
				
				items:[
					{title:"发布"},
					{title:"草稿"},
				],
				current:1
			}
		},
		methods:{
			onClickItem(e){
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
			},
		}
	}
</script>


<style lang="scss">
	.back{
		width: 100%;
		height: 250rpx;
		overflow: hidden;
	}
	.describe{
		width: 100%;
		height: 300rpx;
		position: absolute;
		top: 200rpx;
		border-radius: 20rpx;
		background-color: #FFFFFF;
		.des_img{
			width: 150rpx;
			height: 150rpx;
			border-radius: 50%;
			position: absolute;
			top: -75rpx;
			left: 50rpx;
		}
		
		.info{
			margin: 80rpx 0rpx 0rpx 25rpx;
			background-color: #FFFFFF;
			display: flex;
			text{
				background-color: #FFFFFF;
				font-size: 16px;
				font-weight: 600;
				line-height: 60rpx;
				color: #010206;
			}
			image{
				background-color: #FFFFFF;
				width: 60rpx;
				height: 60rpx;
			}
		}
		
		.manage{
			background-color: #FFFFFF;
			position: absolute;
			top: 0;
			right: 50rpx;
			line-height: 75rpx;
			text{
				font-size: 16px;
				background-color: #FFFFFF;
				color: #010206;
			}
		}
		.medal{
			background-color: #FFFFFF;
			color: #e8f317;
			font-size: 14px;
			font-weight: bold;
			margin-left: 25rpx;
		}
		.introduction{
			background-color: #FFFFFF;
			padding: 10rpx 30rpx 20rpx;
		}
		.home_tab{
			
			.home_tab_title{
				
				position: relative;
				.title_inner{
					
					width: 100%;
					margin: 0 auto;
				}
			}
		}
	}
	
</style>