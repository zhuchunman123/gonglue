<template>
	<view class="content">
		
		<view class="title">选择简略或详细的编辑模式</view>
		
		<view class="mode mode_select_one" @click="handleMode(0)">
			<view class="box_title" >简略模式</view>
			<view class="box_content" :style="{background: gradient}">
				<view class="box_icon"></view>
				<h4 class="box_text">直接编辑图片和文字，快速形成一篇博客</h4>
			</view>
		</view>
		
		<view class="mode mode_select_two" @click="handleMode(1)" >
			<view class="box_title">详细模式</view>
			<view class="box_content" :style="{background: gradients}">
				<view class="box_icon"></view>
				<view class="box_text" >编辑地址，价格，详情，开放时间等</view>
			</view>
		</view>
		
		<view class="button_next_box"><button class="button_next" @click="handleClick">下一步</button></view>
		
	</view>
</template>

<script>
	export default {
		data(){
			return{
				isselect:"",
				start: "",
				end: "",
				starts: "",
				ends: "",
			}
		},
		computed: {
		  	gradient () {
		    	return `linear-gradient(to right, ${this.start}, ${this.end})`
		    },
			gradients () {
				return `linear-gradient(to right, ${this.starts}, ${this.ends})`
			},
		  },
		methods:{
			handleMode(e){
				if(e===0){
					this.isselect=e;
					this.start="#C84E88";
					this.end="#F05E79";
					this.starts="";
					this.ends="";
				}else{
					this.isselect=e;
					this.starts="#C84E88";
					this.ends="#F05E79";
					this.start="";
					this.end="";
				}
			},
			handleClick(){
				if(this.isselect===""){
					uni.showToast({
					  title: "请选择模式",
					  icon: "none"
					});
					return;
				}if(this.isselect===0){
					console.log(233)
					uni.navigateTo({
					  url:"/pages/mine/release/simple/index"
					})
				}if(this.isselect===1){
					console.log(111)
					uni.navigateTo({
					  url:"/pages/mine/release/detailed/index"
					})
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.page{
		background-color: #fff;
	}
	.content{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		.title{
			background-color: #FA7650;
			color: #fff;
			margin-top: 26rpx;
			display: flex;
			justify-content: center;
			align-items: center;
			font-weight: 600;
			font-size: 52rpx;
			height:120rpx ;
			width: 95%;
			border-radius: 10rpx;
			
		}
		.mode{
			.box_title{
				color: #000;
				margin: 30rpx 0;
				font-size: 48rpx;
				font-weight: 600;
				display: flex;
				justify-content: center;
				align-items: center;
			}
			.box_content{
				display: flex;
				width: 500rpx;
				height: 300rpx;
				justify-content: center;
				align-items: center;
				background-color: #ABABAB;
				border-radius: 10rpx;
				.box_icon{
					flex: 1;
				}
				.box_text{
					flex: 2;
					color: #fff;
					font-size: 44rpx;
					font-weight: 500;
					background-color: transparent;
					
					
				} 
			}
		}
		.button_next{
			background-color:#169BD5 ;
			color: #fff;
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: 40rpx;
			width: 300rpx;
			height: 80rpx;
			font-size: 34rpx;
		}
	}
	
</style>
