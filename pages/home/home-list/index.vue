<template>
	<view>
		<view class="list">
			<view class="general">
				<text>实时总榜</text>
				<view class="general_list">
					<view class="general_item">
						<view class="item_left">
							1
						</view>
						<view class="item_middle">
							<view class="title">冰淇淋，化的快 不如来个大圣代 大金链子 小手表 蜜雪冰城就是好 你爱我 我爱你 蜜雪冰城甜蜜蜜 我真的不知道该写什么测试文本了</view>
							<view class="redu">热度103万</view>
						</view>
						<view class="item_right">
							<image src="https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg" mode=""></image>
						</view>
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
	.list{
		.general{
			background-color: #FFFFFF;
			text{
				line-height: 100rpx;
				background-color: #FFFFFF;
				font-size: 16px;
			}
			.general_list{
				
				.general_item{
					height: 150rpx;
					border-top: 2px solid #e5e5e5;
					display: flex;
					background-color: #FFFFFF;
					
					.item_left{
						width: 50rpx;
						height: 50rpx;
						margin: 50rpx 25rpx;
						text-align: center;
						line-height: 50rpx;
						font-weight: bold;
						color: white;
						background-color: #DD524D;
					}
					.item_middle{
						position: absolute;
						left: 100rpx;
						right: 220rpx;
						margin-top: 20rpx;
						background-color: #FFFFFF;
						.title{
							font-size: 14px;
							font-weight: 600;
							display: -webkit-box;
							-webkit-box-orient: vertical; 
							-webkit-line-clamp: 2;
							overflow: hidden;
							background-color: #FFFFFF;
						}
						.redu{
							background-color: #FFFFFF;
							font-size: 12px;
							color: #DCDCDC;
						}
					}
					.item_right{
						position: absolute;
						right: 0;
						height: 130rpx;
						width: 200rpx;
						margin: 10rpx;
						image{
							width: 100%;
							height: 100%;
						}
					}
				}
			}
		}
	}

</style>
