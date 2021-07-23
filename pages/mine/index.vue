<template>
	<view class="mine">
		
		<!-- 头像，昵称，等级展示 ，个人主页页面跳转-->
		<view class="mine_head" v-for="item in personInfo" :key="item.id">
			<image :src="item.image" mode=""></image>
			<view class="head_middle">
				<view class="head_name">{{item.name}}</view>
				
				<!-- 进度条，导入插件 ：cmd-progress进度条组件 -->
				<view class="head_progress">
					<text>LV2</text>
					<progress percent="60" active stroke-width="3" backgroundColor="#999"/>
					<text>LV3</text>
				</view>
			</view>
			<!-- 跳转到个人主页 -->
			<view class="toPersonal">
				个人主页
			</view>
		</view>
		
		<!-- 发布、关注、收藏 -->
		<view class="mine_middle">
			<navigator url="#" style="background-color: #FFFFFF;">
				<h4>关注</h4>
				<p>24</p>
			</navigator>
			<navigator url="#" style="background-color: #FFFFFF;">
				<h4>收藏</h4>
				<p>24</p>
			</navigator>
			<navigator url="#" style="background-color: #FFFFFF;">
				<h4>发布</h4>
				<p>24</p>
			</navigator>
		</view>
		
		<!-- 余额，充值，收入，支出 -->
		<view class="mine_balance">
			<view class="balance_up">
				<h4>账户余额</h4>
				<p>></p>
			</view>
			<view class="balance_down">
				<h4>剩余金币</h4>
				<button type="default">立即充值</button>
			</view>
		</view>
		
		<!-- 各种功能设置 -->
		
		<view class="mine_set">
			<view class="set">
				<view class="set_title">
					<h4>我的设置</h4>
				</view>
			</view>
			<view class="set_content">
				<view class="content_item" v-for="item in sets" :key="item.id">
					<image :src="item.image" mode=""></image>
					<p>{{item.text}}</p>
				</view>
				
			</view>
		</view>

	</view>
</template>

<script>
	
	// 引用组件  cmd-progress进度条组件
	import cmdProgress from "@/components/cmd-progress/cmd-progress.vue"
	export default{
		components:{
			cmdProgress
		},
		data(){
			return{
				
				// 个人信息，头像及昵称
				personInfo:[{
					image:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FwesxSHibU25XbKdJHwcyc9H7tVXwweYA1mjJqz5HtmHnNv9XOSety9PACs4rkwWTiaGG6J1wJial8ibuSpt4KP64BA%2F640&refer=http%3A%2F%2Fmmbiz.qpic.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629517124&t=75040720503a2efe47eb56e85df14943",
					name:"bshdjgbds"
				}],
				
				
				// 设置列表
				sets:[
					{
						image:"../../static/icon/icon_jsqx.png",
						text:"账号与安全",
					},
					{
						image:"../../static/icon/icon_yysj.png",
						text:"认证中心",
					},
					{
						image:"../../static/icon/icon_xsqg.png",
						text:"消息设置",
					},
					{
						image:"../../static/icon/icon-hylb.png",
						text:"在线客服",
					},
					{
						image:"../../static/icon/icon-xydd.png",
						text:"反馈与帮助",
					},
					{
						image:"../../static/icon/icon_yxtj.png",
						text:"关于",
					},
					{
						image:"../../static/icon/icon_jsdz.png",
						text:"创作中心",
					},
					
				]
			}
		}
		
	}
</script>

<style lang="scss">

	.mine_head{
		height: 150rpx;
		
		display: flex;
		margin: 30rpx 0 0 30rpx ;
		
		image{
			
			width: 150rpx;
			height: 150rpx;
			border-radius: 50%;
			margin-right:20rpx;
		}
		.head_middle{
			
			margin-right: 20rpx;
			
			.head_name{
				font-size: 22px;
				line-height: 80rpx;
			}
			.head_progress{
				line-height: 70rpx;
				
				display: flex;
				progress{
					width: 250rpx;
				}
			}
		}
		.toPersonal{
			width: 150rpx;
			height: 50rpx;
			background-color: #007AFF;
			position: absolute;
			right: 0;
			margin: 50rpx 0;
			border-radius: 50rpx 0 0 50rpx;
			font-size: 12px;
			line-height: 50rpx;
			text-align: center;
			color:#FFFFFF;
		}
	}
	
	.mine_middle{
		margin:20rpx;
		height: 120rpx;
		background-color: #FFFFFF;
		border-radius: 20rpx;
		overflow: hidden;
		display: flex;
		navigator{
			flex: 1;
			text-align: center;
			padding: 20rpx 0;
			h4{
				font-size: 16px;
				background-color: #FFFFFF;
				color:#222222;
				font-weight: 600;
			}
			p{
				font-size: 14px;
				background-color: #FFFFFF;
			}
		}
	}
	
	.mine_balance{
		height: 150rpx;
		margin:20rpx;
		padding: 10rpx 20rpx;
		border-radius: 20rpx;
		background-color: #FFFFFF;
		overflow: hidden;
		.balance_up{
			height: 60rpx;
			background-color: #ffffff;
			display: flex;
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
		.balance_down{
			width: 100%;
			height: 70rpx;
			background-color: #FFFFFF;
			
			display: flex;
			
			h4{
				background-color: #FFFFFF;
				line-height: 70rpx;
				
			}
			button{
				
				margin: 5rpx 0;
				height: 60rpx;
				font-size: 12px;
				line-height: 60rpx;
				background-color: #007aff;
				color: #FFFFFF;
				position: absolute;
				right: 40rpx;
			}
		}
	}
	
	.mine_set{
		
		margin:20rpx;
		padding: 10rpx 20rpx;
		border-radius: 20rpx;
		background-color: #FFFFFF;
		overflow: hidden;
		.set{
			height: 60rpx;
			background-color: #ffffff;
			
			.set_title{
				h4{
					background-color: #ffffff;
					line-height: 60rpx;
					font-size: 16px;
					color: #222222;
					font-weight: 600;
				}
			}
		}
		
		.set_content{
			width: 100%;
			display: flex;
			flex-wrap: wrap;
			background-color: #FFFFFF;
			.content_item{
				width: 25%;
				
				background-color: #FFFFFF;
				image{
					width: 80rpx;
					height: 80rpx;
					background-color: #FFFFFF;
					margin: 0 auto;
				}
				p{
					text-align: center;
					background-color: #FFFFFF;
				}
				
			}
			
			
		}
	}
	


</style>