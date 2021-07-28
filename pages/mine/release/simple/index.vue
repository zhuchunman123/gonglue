<template>
	<view>

		<view class="nav-list">
			<navigator hover-class="none" :url="'/pages/basics/' + item.name" class="nav-li" navigateTo
				:class="'bg-'+item.color" :style="[{animation: 'show ' + ((index+1)*0.2+1) + 's 1'}]"
				v-for="(item,index) in elements" :key="index">
				<view class="nav-title">{{item.title}}</view>
				<view class="nav-name">{{item.name}}</view>
				<text :class="'cuIcon-' + item.cuIcon"></text>
			</navigator>
		</view>
		<view class="cu-tabbar-height"></view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				elements: [{
						title: '布局',
						name: 'layout',
						color: 'cyan',
						cuIcon: 'newsfill'
					},
					{
						title: '背景',
						name: 'background',
						color: 'blue',
						cuIcon: 'colorlens'
					},
				],
			};
		},
		onShow() {
			console.log("success")
		}
	}
</script>
<style>
	@import "../../../../styles/colorui/main.css";
	@import "../../../../styles/colorui/icon.css";
</style>
