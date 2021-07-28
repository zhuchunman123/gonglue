<template>
	<scroll-view scroll-y="true" class="information_view" enable-flex="true">
		<view class="info_form">
			<!-- 基础信息	开始 -->
			<view class="info_form_title">
				<view class="info_form_title_text">景区基础信息</view>
			</view>
			<!-- 基础信息	结束 -->
			<view class="info_form_content">
				<!-- 标题	开始 -->
				<view class="input_box">
					<view class="input_title" >*标题</view>
					<input v-model="inputValueTitle" type="text" @input="onKeyInput0" @blur="handleValueTitle" class="input" placeholder="输入标题" maxlength="15">
				</view>
				<!-- 标题	结束 -->
				<!-- 地址	开始 -->
				<view class="input_box">
					<view class="input_title">*地址</view>
					<picker class="input" mode="multiSelector" @columnchange="bindMultiPickerColumnChange"
						:value="multiIndex" :range="multiArray" @change="handleValueAddress">
						<view class="uni-input" style="background-color: #FFFFFF;">
							{{bigAddress}}
						</view>
					</picker>
				</view>
				<!-- 地址	结束 -->
				<!-- 详细地址	开始 -->
				<view class="input_box">
					<view class="input_title">*详细地址</view>
					<input type="text" v-model="inputValueAddress1" @blur="handleValueAddress" class="input" placeholder="输入详细地址" @input="onKeyInput1">
				</view>
				<!-- 详细地址	结束 -->
				<!-- 价格	开始 -->
				<view class="input_box">
					<view class="input_title">价格</view>
					<input v-model="inputValuePrice" type="text" class="input" @input="onKeyInput2" @blur="handleValuePrice">
				</view>
				<!-- 价格	结束 -->
			</view>
		</view>
		<!-- 营业时间	开始 -->
		<view class="business_time">
			<view class="business_time_nav">
				<view class="business_time_title">营业时间</view>
				<view class="business_time_switch_box">
					<switch class="business_time_switch" :checked="isSelected" type="switch" color="#007AFF" @change="switchChange" />
					<view class="">
						{{userDefined}}
					</view>
				</view>
			</view>
			<view class="business_time_content">
				
				<view class="business_time_content_choose_box" v-if="isUserDefined==0" @click="handleMaskOpen">
					<view>
						<view v-if="isChoose===0" class="business_time_content_choose_box_text">{{businessTime}}</view>
						<view v-if="items[0].name===true" class="business_time_content_choose_box_text">
							星期一:{{items[0].timeStart}}——{{items[0].timeEnd}}
						</view>
						<view v-if="items[1].name===true" class="business_time_content_choose_box_text">
							星期二:{{items[1].timeStart}}——{{items[1].timeEnd}}
						</view>
						<view v-if="items[2].name===true" class="business_time_content_choose_box_text">
							星期三:{{items[2].timeStart}}——{{items[2].timeEnd}}
						</view>
						<view v-if="items[3].name===true" class="business_time_content_choose_box_text">
							星期四:{{items[3].timeStart}}——{{items[3].timeEnd}}
						</view> 
						<view v-if="items[4].name===true" class="business_time_content_choose_box_text">
							星期五:{{items[4].timeStart}}——{{items[4].timeEnd}}
						</view>
						<view v-if="items[5].name===true" class="business_time_content_choose_box_text">
							星期六:{{items[5].timeStart}}——{{items[5].timeEnd}}
						</view>
						<view v-if="items[6].name===true" class="business_time_content_choose_box_text">
							星期日:{{items[6].timeStart}}——{{items[6].timeEnd}}
						</view>
					</view>
					
					
				</view>
				
				<!-- 自定义 开始 -->
				<view class="" v-if="isUserDefined==1">
					<view><textarea v-model="inputValueBusinessTime" @input="onKeyInput3_1" placeholder="请输入营业时间" class="info_form_textarea2" 
							auto-height /></view>
				</view>
				<!-- 自定义结束 -->
			</view>

		</view>

		<!-- 营业时间	结束 -->

		<!-- 优惠政策	开始 -->
		<view class="info_form">
			<view class="info_form_title">优惠政策</view>
			<textarea @input="onKeyInput4" v-model="inputValuePreferentialPolicies" placeholder="选填" class="info_form_textarea"  auto-height />
		</view>
		<!-- 优惠政策	结束 -->
		<!-- 实用tips 开始 -->
		<view class="info_form">
			<view class="info_form_title">实用tips</view>
			<textarea  @input="onKeyInput5" v-model="inputValueTips" placeholder="选填" class="info_form_textarea" auto-height />
		</view>
		<!-- 实用tips 结束 -->
		<!-- 详细介绍	开始 -->
		<view class="info_form">
			<view class="info_form_title">详细介绍</view>
			<textarea @input="onKeyInput6" v-model="inputValueIntroduction" placeholder="请输入旅游景点详细介绍" class="info_form_textarea"  auto-height />
		</view>
		<!-- 详细介绍	结束 -->
		<button form-type="submit" class="info_button" @click="handlebutton">下一步</button>
		<!-- 营业时间选择器 -->
		<mask v-if="status===1" @handleMaskStatus="handleStatusChange">
			<view class="mask_content_box">
				<scroll-view scroll-y="true" class="mask_content" enable-flex="true" scrollbars="none">
					<checkbox-group class="checkbox_box">
						<view class="checkbox_box_button">
							<view class="checkbox_box_cancel" @click="handleCancel">取消</view>
							<view class="checkbox_box_sure" @click="handleSure">确定</view>
						</view>

						<view v-for="(item,index) in items" :key="index" class="checkbox_box_items" @click="handle(item.id,item.value)">
							<view class="checkbox_box_items_week">
								<view>{{item.date}}</view>
								<checkbox :checked="item.name" :value="item.value" />
							</view>
							<view v-if="item.name===true" @click.stop="" class="time_choose_box">
								<view class="content_top">
									<view>营业开始时间</view>
									<view>营业结束时间</view>
								</view>
								<view class="content_bottom">
									<view>
										<picker mode="time" start="06:00" end="22:00" @change="bindTimeChangedstart" @click="Start(item.value)">
											<view class="time_choose_text">{{item.timeStart}}</view>
										</picker>
									</view>
									<view>———</view>
									<view>
										<picker mode="time" start="06:00" end="22:00" @change="bindTimeChangedEnd" @click="Start(item.value)">
											<view class="time_choose_text">{{item.timeEnd}}</view>
										</picker>
									</view>
								</view>
							</view>
						</view>
					</checkbox-group>
				</scroll-view>
			</view>
		</mask>
	</scroll-view>
</template>

<script>
	import mask from "../../../../../components/mask.vue";
	export default {
		components: {
			mask
		},
		data() {
			return {
				isSelected:false,
				bigAddress:"亚洲，中国，北京",
				inputValueTitle: "",
				inputValueAddress: "",
				inputValueAddress0:"",
				inputValueAddress1: "",
				inputValuePrice:"",
				inputValueBusinessTime:"",
				inputValuePreferentialPolicies:"",
				inputValueTips:"",
				inputValueIntroduction:"",
				isChoose:0,
				changeindex:"",
				items: [{
						date: "星期一",
						name: false,
						id: 0,
						value: "0",
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期二",
						name: false,
						value: "1",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期三",
						name: false,
						value: "2",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期四",
						name: false,
						value: "3",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期五",
						name: false,
						value: "4",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期六",
						name: false,
						value: "5",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},
					{
						date: "星期日",
						name: false,
						value: "6",
						id: 0,
						timeStart: '08:00',
						timeEnd: '20:00',
					},

				],
				businessTime: "请选择具体时间",
				status: 0,
				isUserDefined: 0,
				userDefined: "是否选择自定义",
				NextTabIndex: "1",
				multiArray: [
					['亚洲', '欧洲'],
					['中国', '日本'],
					['北京', '上海', '广州']
				],
				multiIndex: [0, 0, 0],
			}
		},
		methods: {
			//获取标题内容
			onKeyInput0: function(event) {
			    this.inputValueTitle = event.detail.value
			},
			//获取详细地址内容
			onKeyInput1: function(event) {
			    this.inputValueAddress = event.detail.value
			},
			//获取价格内容
			onKeyInput2: function(event) {
			    this.inputValuePrice = event.detail.value
			},

			onKeyInput3_1: function(event) {
				if(this.isUserDefined===1){
					this.inputValueBusinessTime = event.detail.value
					this.$emit("valueBusinessTime",this.inputValueBusinessTime,this.isUserDefined);
				}else{
					
				}
			},
			//获取优惠价格内容
			onKeyInput4: function(event) {
			    this.inputValuePreferentialPolicies = event.detail.value
				this.$emit("valuePreferentialPolicies",this.inputValuePreferentialPolicies);
			},
			//获取实用tips内容
			onKeyInput5: function(event) {
			    this.inputValueTips = event.detail.value
				this.$emit("valueTips",this.inputValueTips);
			},
			//获取详细介绍内容
			onKeyInput6: function(event) {
			    this.inputValueIntroduction = event.detail.value
				this.$emit("valueIntroduction",this.inputValueIntroduction);
			},
			
			//传递标题内容
			handleValueTitle(){
				this.$emit("valueTitle",this.inputValueTitle);
			},
			//传递详细地址内容
			handleValueAddress(){
				this.bigAddress=this.multiArray[0][this.multiIndex[0]]+"，"+this.multiArray[1][this.multiIndex[1]]+"，"+this.multiArray[2][this.multiIndex[2]]
				this.$emit("valueAddress",this.inputValueAddress,this.multiArray[0][this.multiIndex[0]],this.multiArray[1][this.multiIndex[1]],this.multiArray[2][this.multiIndex[2]]);
			},
			//传递价格内容
			handleValuePrice(){
				this.$emit("valuePrice",this.inputValuePrice);
			},
			//营业时间是否选择
			isChooseHave(){
				var a=0
				for(var i=0;i<7;i++){
					if(this.items[i].name===true){
						a=a+1;
					}
				}if(a>0){
					this.isChoose=1
				}else{
					this.isChoose=0
				}
			},
			Start(e){
				this.changeindex=e
			},
			bindTimeChangedstart(e) {
				this.items[this.changeindex].timeStart = e.detail.value
			},
			bindTimeChangedEnd(e) {
				this.items[this.changeindex].timeEnd = e.detail.value
			},
			handle(e, w) {
				if (e === 1) {
					this.items[w].name = false;
					this.items[w].id = 0;
				} else {
					this.items[w].name = true;
					this.items[w].id = 1;
				}
			},
			handleCancel() {
				this.isChooseHave();
				this.status = 0;
			},
			handleSure() {
				this.isChooseHave();
				this.status = 0;
				if(this.isUserDefined===0){
					var a="",b="",c="",d="",e="",f="",g="";
					if(this.items[0].name===true){
						 a = `星期一:${this.items[0].timeStart}——${this.items[0].timeEnd};`
					}if(this.items[1].name===true){
						 b = `星期二:${this.items[1].timeStart}——${this.items[1].timeEnd};`
					}if(this.items[2].name===true){
						 c = `星期三:${this.items[2].timeStart}——${this.items[2].timeEnd};`
					}if(this.items[3].name===true){
						 d = `星期四:${this.items[3].timeStart}——${this.items[3].timeEnd};`
					}if(this.items[4].name===true){
						 e = `星期五:${this.items[4].timeStart}——${this.items[4].timeEnd};`
					}if(this.items[5].name===true){
						 f = `星期六:${this.items[5].timeStart}——${this.items[5].timeEnd};`
					}if(this.items[6].name===true){
						 g = `星期日:${this.items[6].timeStart}——${this.items[6].timeEnd}.`
					}
					this.inputValueBusinessTime=a+b+c+d+e+f+g
					this.$emit("valueBusinessTime",this.inputValueBusinessTime,this.isUserDefined,this.items[0].name,this.items[0].timeStart,this.items[0].timeEnd,this.items[1].name,this.items[1].timeStart,this.items[1].timeEnd,this.items[2].name,this.items[2].timeStart,this.items[2].timeEnd,this.items[3].name,this.items[3].timeStart,this.items[3].timeEnd,this.items[4].name,this.items[4].timeStart,this.items[4].timeEnd,this.items[5].name,this.items[5].timeStart,this.items[5].timeEnd,this.items[6].name,this.items[6].timeStart,this.items[6].timeEnd);
				}
				
			},
			handleMaskOpen() {
				this.status = 1;
			},
			handleStatusChange(e) {
				this.status = e;
				this.isChooseHave();
			},

			switchChange() {
				if (this.isUserDefined == 0) {
					this.userDefined = "自定义";
					this.isUserDefined = 1;
					this.inputValueBusinessTime="";
					for(var i=0;i<7;i++){
						this.items[i].name=false;
						this.items[i].timeStart="";
						this.items[i].timeEnd="";
					}
				} else {
					this.userDefined = "是否选择自定义";
					this.isChoose=0
					this.isUserDefined = 0;
					
				}
			},
			handlebutton() {
				if(this.inputValueTitle.length>0){
					if(this.inputValueAddress1.length>0){
						this.$emit("tabChange", this.NextTabIndex);
					}else{
						uni.showToast({
						  title: "请输入详细地址",
						  icon: "none"
						});
						return;
					}
				}else{
					uni.showToast({
					  title: "请输入标题",
					  icon: "none"
					});
					return;
				}
			},
			bindTimeChangeStart: function(e) {
				this.time = e.detail.value
			},
			bindTimeChangeEnd: function(e) {
				this.time = e.detail.value
			},

			//地址选择器
			bindMultiPickerColumnChange: function(e) {
				// console.log('修改的列为：' + e.detail.column + '，值为：' + e.detail.value)
				this.multiIndex[e.detail.column] = e.detail.value
				switch (e.detail.column) {
					case 0: //拖动第1列
						switch (this.multiIndex[0]) {
							case 0:
								this.multiArray[1] = ['中国', '日本']
								this.multiArray[2] = ['北京', '上海', '广州']
								break
							case 1:
								this.multiArray[1] = ['英国', '法国']
								this.multiArray[2] = ['伦敦', '曼彻斯特']
								break
						}
						this.multiIndex.splice(1, 1, 0)
						this.multiIndex.splice(2, 1, 0)
						break
					case 1: //拖动第2列
						switch (this.multiIndex[0]) { //判断第一列是什么
							case 0:
								switch (this.multiIndex[1]) {
									case 0:
										this.multiArray[2] = ['北京', '上海', '广州']
										break
									case 1:
										this.multiArray[2] = ['东京', '北海道']
										break
								}
								break
							case 1:
								switch (this.multiIndex[1]) {
									case 0:
										this.multiArray[2] = ['伦敦', '曼彻斯特']
										break
									case 1:
										this.multiArray[2] = ['巴黎', '马赛']
										break
								}
								break
						}
						this.multiIndex.splice(2, 1, 0)
						break
				}
			},
		}
	}
</script>

<style lang="scss">
	.time_choose_text{
		padding: 10rpx;
		border-bottom: 3rpx solid #C0C0C0;
		
	}
	.time_choose_box {
		justify-content: space-around;
		align-items: center;
		display: flex;
		width: 100%;
		padding: 40rpx 0;
		flex-direction: column;
		
		.content_top{
			font-size: 40rpx;
			width: 90%;
			display: flex;
			justify-content: space-around;
			align-items: center;
			
		}
		.content_bottom{
			font-size: 36rpx;
			padding: 30rpx;
			width: 80%;
			display: flex;
			justify-content: space-around;
			align-items: center;
			
		}
	}

	.checkbox_box_button {
		border-bottom: 5rpx solid #aaa;
		position: fixed;
		justify-content: space-between;
		border-top-right-radius: 50rpx;
		border-top-left-radius: 50rpx;
		align-items: center;
		width: 100%;
		display: flex;
		padding: 30rpx 30rpx;
		top: 10.5%;
		font-size: 42rpx;
		z-index: 199;
		

		.checkbox_box_cancel {
			background-color: transparent ;
		}
		.checkbox_box_sure {
			background-color: transparent ;
		}
	}
 
	.checkbox_box_items {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		width: 750rpx;

		.checkbox_box_items_week {
			display: flex;
			justify-content: space-between;
			padding: 40rpx;
			align-items: center;
			font-size: 38rpx;
			width: 750rpx;
		}
	}

	.checkbox_box {
		margin-top: 90rpx;
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.mask_content {
		height: 100%;
		padding: 40rpx 0 40rpx 0;
		width: 750rpx;
	}

	.mask_content_box {

		display: flex;
		width: 890rpx;
		height: 100%;
		overflow: hidden;
	}

	.info_form_textarea2 {
		min-height: 84.375rpx;
		background-color: #fff;

		font-size: 38rpx;
		width: 625rpx;
		border-radius: 10rpx;
	}

	.business_time {
		margin-left: 37.5rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		width: 90%;

		.business_time_nav {
			width: 100%;
			display: flex;
			justify-content: flex-start;
			align-items: center;
			margin-top: 30rpx;
			margin-bottom: 30rpx;

			.business_time_title {
				font-size: 30rpx;
				margin-right: 37.5rpx;
			}

			.business_time_switch_box {
				display: flex;
				justify-content: flex-start;
				align-items: center;

				.business_time_switch {}
			}
		}

		.business_time_content {
			border: 5rpx solid #dddddd;
			background-color: #FFF;
			width: 100%;
			padding: 20rpx;

			.business_time_content_choose_box {
				min-height: 46.875rpx;
				font-size: 40rpx;
				.business_time_content_choose_box_text{
					background-color:#fff;
				}
			}
		}

	}


	.info_form_textarea {
		min-height: 84.375rpx;
		padding: 15rpx;
		background-color: #fff;
		border: 5rpx solid #dddddd;
		font-size: 38rpx;
		width: 637.5rpx;
		border-radius: 10rpx;
	}

	.information_view {
		height: calc(100vh - 80rpx);

		.info_form {
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;

			.info_form_title {
				width: 90%;
				font-size: 30rpx;
				margin: 30rpx 0;
			}

			.info_form_content {
				width: 90vw;

				.input_box {
					border-bottom: 5rpx solid #f4f4f4;
					background-color: #FFFFFF;
					display: flex;
					justify-content: center;
					align-items: center;
					height: 100rpx;
					border-radius: 5rpx;

					.input_title {
						flex: 1;
						justify-content: center;
						align-items: center;
						display: flex;
						background-color: #FFFFFF;
					}

					.input {
						flex: 3;
						background-color: #FFFFFF;
					}
				}
			}
		}

		.info_introduction {}

		.info_button {
			margin-top: 50rpx;
			margin-bottom: 50rpx;
			color: #fff;
			font-weight: 600;
			width: 280rpx;
			height: 80rpx;
			background-color: #39b54a;
			border-radius: 40rpx;
			font-size: 34rpx;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
</style>
