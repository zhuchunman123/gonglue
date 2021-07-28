<template>
	<view>
		<scroll-view class="scroll-h" :scroll-x="true">
			<view v-for="(tab,index) in tabBars" :key="tab.id" class="uni-tab-item" :id="tab.id" :data-current="index"
				@click="ontabtap">
				<text class="uni-tab-item-title"
					:class="tabIndex==index ? 'uni-tab-item-title-active' : ''">{{tab.name}}</text>
			</view>
		</scroll-view>
		<view class="line-h"></view>
		<view class="home_tab_content">
			<view v-show="tabIndex == 0">
				<information @tabChange="handlebuttonAction" @valueTitle="getValueTitle" @valueAddress="getValueAddress" @valuePrice="getValuePrice" @valueBusinessTime="getValueBusinessTime" @valuePreferentialPolicies="getValuePreferentialPolicies" @valueTips="getValueTips" @valueIntroduction="getValueIntroduction"></information>
			</view>
			<view v-show="tabIndex == 1">
				<album @tabChange="handlebuttonAction"></album>
			</view>
			<view v-show="tabIndex == 2" :CurrentTabIndex="tabIndex">
				<route></route>
			</view>
			<view v-show="tabIndex == 3">
				<ScenicSpot></ScenicSpot>
			</view>
			<view v-show="tabIndex == 4">
				<ScenicSpot></ScenicSpot>
			</view>
			
		</view>
	</view>
</template>

<script>
	import information from "./Information/index.vue";
	import route from "./route/index.vue";
	import ScenicSpot from "./ScenicSpot/index.vue";
	import album from "./album/index.vue";
	import {
		uniSegmentedControl
	} from "@dcloudio/uni-ui";
	export default {
		components: {
			uniSegmentedControl,
			information,
			route,
			ScenicSpot,
			album
		},
		data() {
			return {
				value:[
					{q:"",y:"",o:"",s:"",g:"",k:"",x:"",time0Start:"08:00",time1Start:"08:00",time2Start:"08:00",time3Start:"08:00",time4Start:"08:00",time5Start:"08:00",time6Start:"08:00",time0End:"20:00",time1End:"20:00",time2End:"20:00",time3End:"20:00",time4End:"20:00",time5End:"20:00",time6End:"20:00",valueTitle:"",valueAddress:"",valuePrice:"",valueAddress1:"",valueAddress0:"亚洲，中国，北京",valueBusinessTime:"",isUserDefined:"",valuePreferentialPolicies:"",valueTips:"",valueIntroduction:""},
				],
				tabIndex: 1,
				tabBars: [{
					name: '详细信息',
					id: 'guanzhu'
				},
				{
					name: '相册及视频',
					id: 'caijing'
				},
				{
					name: '路线',
					id: 'tuijian'
				}, 
				
				{
					name: '景点A',
					id: 'tiyu'
				}, {
					name: '景点B',
					id: 'redian'
				},
				{
					name: '景点B',
					id: 'redian'
				},
				],
			}
		},
		methods: {
			getValueTitle(e){
				this.value[0].valueTitle=e
			},
			getValueAddress(w,e,r,q){
				this.value[0].valueAddress1=`${w}`
				this.value[0].valueAddress0=`${e},${r},${q}`
				this.value[0].valueAddress=`${w}${e}${r}${q}`
			},
			getValuePrice(e){
				this.value[0].valuePrice=e
			},
			getValueBusinessTime(e,w,q,r,t,y,u,i,o,p,a,s,d,f,g,h,j,k,l,z,x,c,v){
				this.value[0].valueBusinessTime=e
				this.value[0].isUserDefined=w
				this.value[0].q=q
				this.value[0].y=y
				this.value[0].o=o
				this.value[0].s=s
				this.value[0].g=g
				this.value[0].k=k
				this.value[0].x=x
				this.value[0].time0Start=r
				this.value[0].time1Start=u
				this.value[0].time2Start=p
				this.value[0].time3Start=d
				this.value[0].time4Start=h
				this.value[0].time5Start=l
				this.value[0].time6Start=c
				this.value[0].time0End=t
				this.value[0].time1End=i
				this.value[0].time2End=a
				this.value[0].time3End=f
				this.value[0].time4End=j
				this.value[0].time5End=z
				this.value[0].time6End=v
			},
			getValuePreferentialPolicies(e){
				this.value[0].valuePreferentialPolicies=e
			},
			getValueTips(e){
				this.value[0].valueTips=e
			},
			getValueIntroduction(e){
				this.value[0].valueIntroduction=e
			},
			ontabtap(e) {
				this.tabIndex = e.currentTarget.dataset.current;
				
			},

			
			//下一步按钮
			handlebuttonAction(e){
				this.tabIndex=e
			}
		},
	}
</script>

<style lang="scss" scoped>
	.scroll-h {
		width: 750rpx;
		width: 100%;
		height: 80rpx;
		flex-direction: row;
		white-space: nowrap;
		
	}

	.line-h {
		height: 1rpx;
		background-color: #cccccc;
	}

	.uni-tab-item {
		display: inline-block;
		flex-wrap: nowrap;
		padding-left: 34rpx;
		padding-right: 34rpx;
	}

	.uni-tab-item-title {
		color: #555;
		font-size: 30rpx;
		height: 80rpx;
		line-height: 80rpx;
		flex-wrap: nowrap;
		/* #ifndef APP-PLUS */
		white-space: nowrap;
		/* #endif */
	}

	.uni-tab-item-title-active {
		color: #007AFF;
		padding-bottom: 10rpx;
		border-bottom: 2rpx solid #007AFF;
	}
</style>
