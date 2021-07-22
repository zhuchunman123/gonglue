<template>
	<view>
		
		<view class="general">
			<text style="line-height: 100rpx;background-color: #FFFFFF;font-size: 16px;">实时总榜</text>
			<view class="general_list">
				<view class="general_item">
					<view class="box1">
						1
					</view>
					<view class="content">
						
					</view>
				</view>
			</view>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data(){
			return {
			
			};
		},
		mounted() {
			
		}
	}
</script>

<style lang="scss" scoped>
	.general{
		background-color: #FFFFFF;
		.general_list{
			
			.general_item{
				height: 150rpx;
				border: 1px solid #007AFF;
				display: flex;
				background-color: #FFFFFF;
				
				.box1{
					width: 50rpx;
					height: 50rpx;
					margin: 50rpx;
					text-align: center;
					line-height: 50rpx;
					font-weight: bold;
					color: white;
					background-color: #DD524D;
				}
				.content{
					
				}
			}
		}
	}
</style>
