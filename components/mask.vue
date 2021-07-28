<template>
	<view>
		<view class="cptmask" @click="handleMaskClose">
		</view>
		<view class="mask_box" @click.stop="">
			<slot></slot>
		</view>
	</view>
</template>
<script>
	export default {
		methods: {
			handleMaskClose() {
				this.$emit("handleMaskStatus", this.status);
			}
		},
		data() {
			return {
				status: 0
			}
		}
	}
</script>

<style lang="scss">
	.mask_box {
		z-index: 100;
		height: 90%;
		width: 100%;
		position: fixed;
		bottom: 0;
		border-top-right-radius: 50rpx;
		border-top-left-radius: 50rpx;
		
	}

	.cptmask {
		background-color: #000000;

		opacity: 0.5;
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 98;
	}
</style>
