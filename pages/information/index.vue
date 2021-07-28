<template>
	<view class="info">
		
		<!-- 常规通知  点赞，关注，评论以及回复 -->
		<view class="info_normal">
			<text class="iconfont icondianzan"></text>
			<h4>点赞</h4>
			<p>></p>
		</view>
		<view class="info_normal">
			<text class="iconfont iconhot"></text>
			<h4>关注</h4>
			<p>></p>
		</view>
		<view class="info_normal">
			<text class="iconfont iconpinglun"></text>
			<h4>评论与回复</h4>
			<p>></p>
		</view>
		
	</view>
    
</template>

<script>
	
    export default {
    }
	
</script>

<style lang="scss" scoped>
	
	.info_normal{
		height: 80rpx;
		background-color: #ffffff;
		padding: 10rpx 20rpx;
		margin-top: 10rpx;
		display: flex;
		
		.iconfont {
			font-size: 25px;
			line-height: 60rpx;
			margin-right: 10rpx;
			background-color: #FFFFFF;
			
		}
		h4{
			line-height: 60rpx;
			font-size: 16px;
			color: #222222;
			font-weight: 600;
			width: 95%;
			background-color: #FFFFFF;
		}
		p{
			line-height: 60rpx;
			font-size: 20px;
			width: 5%;
			background-color: #FFFFFF;
		}
	}

</style>
