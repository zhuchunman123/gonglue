<template>
	<scroll-view scroll-y="true" class="album_view" enable-flex="true">
		<!-- 图片 -->
		<view class="image_box">
			<form>
				<view class="cu-bar bg-white">
					<view class="action">
						图片上传
					</view>
					<view class="action">
						{{imgList.length}}/18
					</view>
				</view>
				<view class="cu-form-group">
					<view class="grid col-4 grid-square flex-sub background_white">
						<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage"
							:data-url="imgList[index]">
							<image :src="imgList[index]" mode="aspectFill"></image>
							<view class="cu-tag bg-red " @tap.stop="DelImg" :data-index="index">
								<text class='cuIcon-close background_no'></text>
							</view>
						</view>
						<view class="solids" @tap="ChooseImage" v-if="imgList.length<18">
							<text class='cuIcon-cameraadd'></text>
						</view>
					</view>
				</view>
		
			</form>
		</view>
		
		<!-- 视频 -->
		<view class="video_box">
			<form>
				<view class="cu-bar bg-white">
					<view class="action">
						视频上传
					</view>
					<view class="action">
						{{videoList.length}}/9
					</view>
				</view>
				<view class="cu-form-group">
					<view class="grid col-4 grid-square flex-sub background_white">
						<view class="bg-img" v-for="(item,index) in videoList" :key="index"
							:data-url="videoList[index]">
							<video :src="videoList[index]" mode="aspectFill" ></video>
							<view class="cu-tag bg-red " @tap.stop="DelVideo" :data-index="index">
								<text class='cuIcon-close background_no'></text>
							</view>
						</view>
						<view class="solids" @tap="ChooseVideo" v-if="videoList.length<9">
							<text class='cuIcon-video'></text>
						</view>
					</view>
				</view>
			</form>
		</view>
		<view class="button" @click="handlebutton">
			下一步
		</view>
	</scroll-view>
	
</template>
<script>
	export default {
		
		data() {
			return {
				imgList: [],
				videoList:[],
				NextTabIndex:"2",
			};
		},
		methods: {
			handlebutton(){
				console.log(233)
				this.$emit("tabChange", this.NextTabIndex);
			},
			ChooseVideo(){
				uni.chooseMedia({
					mediaType:"video",
					sourceType: ['album'], //从相册选择
					success:(res)=>{
						var a=[]
						a.splice(-1,0,res.tempFiles[0].tempFilePath)
						if (this.videoList.length != 0) {
							this.videoList = this.videoList.concat(a)
						} 
						else {
							this.videoList = a
						}
					}
				})
			},
			ChooseImage() {
				uni.chooseImage({
					count: 18, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: (res) => {
								if (this.imgList.length != 0) {
									this.imgList = this.imgList.concat(res.tempFilePaths)
								} else {
									this.imgList = res.tempFilePaths
								}
							}
						// const tempFilePaths = res.tempFilePaths;
						// const uploadTask = uni.uploadFile({
						// 	url: 'http://47.xxx.xxx.78:8088/chemApp/work/upload.action',
						// 	filePath: tempFilePaths[0],
						// 	name: 'file',
						// 	success: function(uploadFileRes) {
						// 		console.log(uploadFileRes);
						// 		_this.imgList = [..._this.imgList, uploadFileRes.data]
						// 	}
						// });
					})
				
			},
			ViewImage(e) {
				uni.previewImage({
					urls: this.imgList,
					current: e.currentTarget.dataset.url
				});
			},
			//删除
			DelImg(e) {
				uni.showModal({
					title: '删除',
					content: '确定要删除这张图片？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.imgList.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
			DelVideo(e){
				uni.showModal({
					title: '删除',
					content: '确定要删除这个视频？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							var a=[];
							var b=this.videoList.__ob__.value.splice(e.currentTarget.dataset.index, 1)
							this.imgVideo=b
						}
					}
				})
			}
		}
	}
</script>

<style scoped>
	@import "../../../../../styles/colorui/main.css";
	@import "../../../../../styles/colorui/icon.css";
	.background_no{
		background-color: transparent ; 
	}
	.background_white{
		background-color: #FFF;
	}
	
	.button{
		color: #FFFFFF;
		font-size: 34rpx;
		margin: 70rpx 0 70rpx 235rpx ;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 280rpx;
		height: 80rpx;
		font-weight: 600;
		border-radius: 40rpx;
		background-color: #9c26b0;
	}
	.image_box{
		margin-top: 40rpx;
	}
	.video_box{
		margin-top:40rpx ;
	}
	.cu-form-group{
		min-height: 400rpx;
	}
	.album_view{
		margin-top: 1rpx;
		background-color: #f1f1f1;
		height: calc(100vh - 80rpx);
		font-size: 28upx;
		color: #333333;
		font-family: Helvetica Neue, Helvetica, sans-serif;
	}
	.action{
		background-color: #FFFFFF;
	}
</style>
