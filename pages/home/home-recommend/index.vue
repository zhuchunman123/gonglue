<template>
	<view>
		
		<!-- 列表开始 -->
		<view class="recommend_list" >
			<navigator class="recommend_item"
			url="/pages/details/details"
			v-for="item in recommend"
			:key="item.id"
			>
				<!-- 左侧图片 -->
				<view class="recommend_img">
					<image :src="item.img" mode=""></image>
				</view>
				<!-- 右侧示例信息 -->
				<view class="recommend_info">
					<view class="recommend_title">{{item.title}}</view>
					<view class="recommend_label">{{item.label}}</view>
					
					<view class="recommend_add">
						<view class="recommend_head">
							<image :src="item.head" mode=""></image>
						</view>
						<view class="recommend_nickname">{{item.nickname}}</view>
						<view class="recommend_see">{{item.see}}浏览量</view>
						<view class="recommend_function">...</view>
					</view>
				</view>
			</navigator>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data(){
			return {
			//列表数组
			recommend:[
				{img:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				title:"标题1",
				label:"标签1",
				head:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				nickname:"昵称",
				see:18,
				
				},
				{img:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				title:"标题2",
				label:"标签2",
				head:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				nickname:"昵称",
				see:18,
				},
				{img:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				title:"标题2",
				label:"标签2",
				head:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				nickname:"昵称",
				see:18,
				},
				{img:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				title:"标题2",
				label:"标签2",
				head:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
				nickname:"昵称",
				see:18,
				}
			]
			};
		},
		mounted() {
			
		}
		
	}
</script>

<style lang="scss" scoped>
	.recommend_list{
		padding: 0;
		.recommend_item{
			height: 180rpx;
			padding: 0;
			display: flex;
			background-color: #FFFFFF;
			margin-top: 5rpx;
			
			.recommend_img{
				flex: 1;
				margin: 10rpx;
				overflow: hidden;
				border: 1px solid #007AFF;
				image{
				width: 100%;
				height: 100%;
					
				}
			}
			.recommend_info{
				background-color: #FFFFFF;
				flex: 2;
				padding: 0 10rpx;
				.recommend_title{
					background-color: #FFFFFF;
					font-size: 30rpx;
					color: #000;
					padding: 10rpx 0;
				}
				.recommend_label{
					background-color: #FFFFFF;
					display: inline-block;
					height: 40rpx;
					font-size: 14rpx;
					border: 1px solid #DD524D;
					border-radius: 20rpx;
					text-align: center;
					line-height: 40rpx;
					padding: 0 10rpx;
					
				}
				.recommend_add{
					background-color: #FFFFFF;
					display: flex;
					padding: 10rpx 0;
					line-height: 50rpx;
					
					.recommend_head{
						
						width: 50rpx;
						height: 50rpx;
						overflow: hidden;
						border-radius: 50%;
						
						.img{
							width: 100%;
							height: 100%;
						}
						margin-right: 5rpx;
						
					}
					.recommend_nickname{
						margin-right: 30rpx;
						background-color: #FFFFFF;
					}
					.recommend_see{
						font-size: 20rpx;
						background-color: #FFFFFF;
					}
					.recommend_function{
						float: right;
						background-color: #FFFFFF;
					}
				}
			}
		}
	}
</style>
