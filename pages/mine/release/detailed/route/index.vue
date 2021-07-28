<template>
	<view >
		<map name="" :latitude="latitude" :longitude="longitude" class=""></map>
	</view>
</template>
<script>
	import amap from '../../../../../utils/amap-wx.js';
	export default {
		props:{
			CurrentTabIndex:Number
		},
		data() {
			return {
				hasLocation: false,
				location: {},
				amapPlugin: null,
				key: 'bc892c1eedfdd7047f123100b0de6c3c',
				addressName: '',
				tabIndex: 2,
				latitude: "",
				longitude: "",
				weather: {
					hasData: false,
					data: []
				}
			}
		},
		mounted() {
			this.amapPlugin = new amap.AMapWX({
				key: this.key,
			});
			this.getRegeo()
		},
		methods: {
			//获取位置详细信息

			getRegeo() {
					this.amapPlugin.getRegeo({
						success: (data) => {
							this.addressName = data[0].name;
							this.latitude = data[0].latitude;
							this.longitude = data[0].longitude;
							uni.hideLoading();
						},
						fail: (info) => {
							console.log(info.errMsg)
						}
					});
				

			},


			getWeather() {
				uni.showLoading({
					title: '获取信息中'
				});
				this.amapPlugin.getWeather({
					success: (data) => {
						for (const key in data) {
							if (key !== 'liveData') {
								this.weather.data.push({
									name: 'div',
									children: [{
										type: 'text',
										text: data[key].text + '：' + data[key].data
									}]
								});
							}
						}
						uni.hideLoading();
						this.weather.hasData = true;
					}
				});
			}
		}
	}
</script>

<style>
	view {
		display: block;
	}

	.page {
		display: flex;
		flex: 1;
		justify-content: center;
		flex-direction: column;
		width: 750upx;
		text-align: center;
	}


	.btn-list button {
		margin: 20upx;
	}
</style>
