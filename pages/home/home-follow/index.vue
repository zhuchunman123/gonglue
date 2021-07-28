<template>
	<view class="follow">
		
		<view class="follow_list" >
			<view class="follow_item" v-for="item in folloList" :key="item.id">
				<!-- 头部 头像昵称时间  -->
				<view class="follow_header">
					<view class="header_head"><image :src="item.headImage" mode=""></image></view>
					<view class="header_middle">
						<view class="header_nickname">{{item.nickName}}</view>
						<view class="header_time">{{item.time}}</view>
					</view>
					<view class="function">···</view>
				</view>
				
				<!-- 中间内容图片 -->
				<view class="follow_img">
					<image :src="item.followImg" mode="widthFix"></image>
				</view>
				
				<!-- 底部点赞收藏等信息 -->
				<view class="follow_footer">
					<view class="footer_title">{{item.title}}</view>
					<view class="footer_addInfo">
						<text class="iconfont icondianzan">{{item.dianzan}}</text>
						<text class="iconfont iconshoucang">{{item.shoucang}}</text>
						<text class="iconfont iconpinglun">{{item.pinglun}}</text>
						<text class="iconfont iconzhuanfa">{{item.zhuanfa}}</text>
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
				
				// 测试数据
				folloList:[
					{
						headImage:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
						nickName:"昵称",
						time:"2021-09-18  12：00",
						followImg:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
						title:"这是标题这是标题这是标题这是标题这是标题这是标题这是标题这是标题这是标题",
						dianzan:128,
						shoucang:128,
						pinglun:128,
						zhuanfa:128
					},
					{
						headImage:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
						nickName:"昵称",
						time:"2021-09-18  12：00",
						followImg:"https://img1.baidu.com/it/u=4110196045,3829597861&fm=26&fmt=auto&gp=0.jpg",
						title:"这是标题这是标题这是标题这是标题这是标题这是标题这是标题这是标题这是标题",
						dianzan:128,
						shoucang:128,
						pinglun:128,
						zhuanfa:128
					}
				]
			}
		},
		mounted() {
			
		}
	}
		
</script>

<style lang="scss" scoped>
	.follow_list{
		.follow_item{
			background-color: #FFFFFF;
			width: 100%;
			
			.follow_header{
				display: flex;
				padding: 5rpx 10rpx;
				height: 100rpx;
				background-color: #FFFFFF;
				
				margin-bottom: 5rpx;
				.header_head{
					width: 80rpx;
					height: 80rpx;
					background-color: #FFFFFF;
					border-radius: 50%;
					overflow: hidden;
					margin-right: 10rpx;
					image{
						width: 100%;
						height: 100%;
					}
					
				}
				.header_middle{
					flex: 9;
					background-color: #FFFFFF;
					.header_nickname{
						background-color: #FFFFFF;
						height: 60rpx;
						line-height: 60rpx;
						font-size: 16px;
						
					}
					.header_time{
						background-color: #FFFFFF;
						height: 20rpx;
						line-height: 20rpx;
						font-size: 10px;
					}
				}
				.function{
					background-color: #FFFFFF;
					flex:1;
					line-height: 100rpx;
					font-size: 24px;
					
					
				}
			}
			.follow_img{
				height: 300rpx;
				overflow: hidden;
				image{
					width: 100%;
					height: 100%;
				}
			}
			.follow_footer{
				
				margin: 5rpx 10rpx;
				background-color: #FFFFFF;
				height: 120rpx;
				.footer_title{
					background-color: #FFFFFF;
					line-height: 40rpx;
					
					font-size: 16px;
					font-weight: bold;
					overflow: hidden;
					text-overflow:ellipsis;
					white-space:nowrap;
					
				}
				.footer_addInfo{
					
					margin: 0 10rpx;
					line-height: 80rpx;
					display: flex;
					.iconfont{
						background-color: #FFFFFF;
						flex: 1;
					}
				}
			}
			
		}
	}
</style>
