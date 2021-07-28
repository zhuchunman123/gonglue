<template>
	<view>
		<view class="total">
			<h3>余额</h3>
			<p>{{389}}</p>
			<h4>充值规则>>></h4>
		</view>
		<view class="chongzhi">
			<p>充值</p>
			<view class="c_list" v-for="item in cList" :key="item.id">
				<view class="c_item">
					{{item.a}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				// 充值金额选择
				cList:[
					
				]
			}
		}
	}
</script>

<style lang="scss" scoped>
	
	.total{
		height: 150rpx;
		margin: 10rpx 20rpx;
		background-color: #836890;
		border-radius: 20rpx 20rpx 0 0 ;
		color: #FFFFFF;
		text-align: center;
		h3{
			line-height: 50rpx;
		}
		p{
			font-size: 16px;
			line-height: 60rpx;
		}
		h4{
			font-size: 10px;
			line-height: 40rpx;
		}
	}
	.chongzhi{
		height: 300rpx;
		width: 100%;
		background-color: #FFFFFF;
		position: absolute;
		top: 150rpx;
		border-radius: 20rpx;
		
		p{
			margin: 10rpx 20rpx;
			font-size: 18px;
			
		}
		
		.c_list{
			background-color: #FFFFFF;
			display: flex;
			
			.c_item{
				width: 20%;
				height: 50rpx;
				background-color: #F0F0F0;
			}
		}
	}
</style>
