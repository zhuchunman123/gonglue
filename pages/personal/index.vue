<template>
	
	<view>
		<!-- 背景 -->
		<view class="back">
			<image src="https://ss0.baidu.com/94o3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/cb8065380cd791230f4870a5ac345982b3b780b3.jpg" mode=""></image>
		</view>
		
		<!-- 个人信息 -->
		<view class="describe">
			<image class="des_img" src="https://ss0.baidu.com/94o3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/cb8065380cd791230f4870a5ac345982b3b780b3.jpg" mode=""></image>
			<navigator class="info" url="data_edit">
				<text>我是一个粉刷匠</text>
				<image src="../../static/icon/写字版.png" mode=""></image>
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		
		data(){
			return {
				
			}
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
			margin: 75rpx 0rpx 0rpx 25rpx;
			background-color: #FFFFFF;
			display: flex;
			text{
				background-color: #FFFFFF;
				font-size: 16px;
				font-weight: 600;
				line-height: 60rpx;
			}
			image{
				background-color: #FFFFFF;
				width: 60rpx;
				height: 60rpx;
			}
		}
	}
	
</style>