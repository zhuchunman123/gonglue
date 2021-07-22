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
				personInfo:[{
					image:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FwesxSHibU25XbKdJHwcyc9H7tVXwweYA1mjJqz5HtmHnNv9XOSety9PACs4rkwWTiaGG6J1wJial8ibuSpt4KP64BA%2F640&refer=http%3A%2F%2Fmmbiz.qpic.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1629517124&t=75040720503a2efe47eb56e85df14943",
					name:"bshdjgbds"
				}]
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
			}
			p{
				font-size: 14px;
			}
		}
	}
	
	.mine_balance{
		height: 150rpx;
		background-color: #FFFFFF;
	}
	

</style>