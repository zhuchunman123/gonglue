<template>
	
	<!-- 个人资料的编辑页 -->
	<view class="edit">
		<view class="touxiang">
			<p>头像</p>
			<text class="iconfont iconiconfontjiantou4"></text>
		</view>
		<view class="nicheng">
			<p>昵称</p>
			<text class="iconfont iconiconfontjiantou4"></text>
		</view>
		<view class="xingbie">
			<p>性别</p>
			<text class="iconfont iconiconfontjiantou4"></text>
		</view>
		<view class="jianjie">
			<p>简介</p>
			<text class="iconfont iconiconfontjiantou4"></text>
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
	.edit{
		
		.touxiang{
			margin-top: 20rpx;
			height: 100rpx;
			background-color: #FFFFFF;
			display: flex;
		}
		.nicheng{
			margin-top: 5rpx;
			height: 100rpx;
			background-color: #FFFFFF;
			display: flex;
		}
		.xingbie{
			margin-top: 5rpx;
			height: 100rpx;
			background-color: #FFFFFF;
			display: flex;
		}
		.jianjie{
			margin-top: 5rpx;
			height: 100rpx;
			background-color: #FFFFFF;
			display: flex;
		}
		
		p{
			line-height: 100rpx;
			font-size: 16px;
			font-weight: bold;
			margin-left: 20rpx;
		}
		text{
			background-color: #FFFFFF;
			line-height: 100rpx;
			position: absolute;
			right: 20rpx;
		}
	}

</style>
