<template>
	<scroll-view scroll-y="true" class="album_box" enable-flex="true">
		<view class="content_box">
			<view class="Choose_text">选择图片</view>
			<view class="imageChoose_box">
				<uni-file-picker ref="selectImage" class="imageChoose" auto-upload="false" v-model="imageValue" file-mediatype="image" mode="grid" file-extname="png,jpg" @select="imageSelect"
					></uni-file-picker>
			</view>
			<view class="Choose_text">选择视频</view>
			<view class="videoChoose_box">
				<uni-file-picker class="videoChoose" v-model="videoValue" file-mediatype="video" mode="grid"
					></uni-file-picker>
			</view>
		</view>
		<view class="button_box"><view class="button" @click="imageFail">下一步</view></view>
		
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				imageValue:[]
			}
		},
		methods: {
			imageSelect(){
				console.log()
				
			},
			imageFail(){
				uni.uploadFile({
					
				})
				console.log(this.$refs.selectImage.tempFilePaths)
			}
		},
		mounted() {
		}
	}
</script>

<style lang="scss" scoped>
	.information_view{
		background-color: red;
	}
	.album_box {
		width: 100%;
		height: calc(100vh - 80rpx);
		.content_box {
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			.Choose_text{
				display: flex;
				align-items: center;
				font-size: 40rpx;
				margin: 40rpx;
				height: 100rpx;
				width: 100%;
				padding-left:60rpx;
				background-color: #f8f8f8;
			}
			.imageChoose_box{
				display: flex;
				justify-content: center;
				align-items: center;
				width: 680rpx;
				height: 100%;
				.imageChoose{
					width: 100%;
					height: 100%;
				}
			}
			.videoChoose_box{
				display: flex;
				justify-content: flex-start;
				align-items: center;
				width: 680rpx;
				height: 100%;
				.videoChoose{

				}
			}
		}
		.button_box{
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: 100rpx;
			.button {
			display: flex;
			justify-content: center;
			align-items: center;
			width: 280rpx;
			height: 80rpx;
			color: #fff;
			font-weight: 600;
			font-size: 34rpx;
			border-radius: 10rpx;
			background-color: #169BD5;
		}
		}
		
	}
</style>
