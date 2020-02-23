<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="bg-white" style="height: 60upx;"></view>
		<view class="bg-white" style="">
			<view class="padding ">
				<view class="padding-lr bg-white" style="border: #555555 1upx solid; border-radius: 15upx; height: 1110upx;">
					<view class="vol_img">
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_1" style="width: 50upx; height: 80upx;"></image>
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_2" style="width: 50upx; height: 80upx;"></image>
					</view>
					<view class="text-center margin-top">
						<text class="text-xl text-black ">登录</text>
					</view>
					<form  @submit="formSubmit">
						<view class="" style="margin: 10upx 60upx;">
							<view class="padding-top">
								<input class="uni-input" placeholder="请输入用户名" name="user" focus />
							</view>
							<view class="padding-top">
								<input class="uni-input" maxlength="50" placeholder="请输入密码"  name="pass" focus password type="text"/>
							</view>

							<view class="padding-top">
								<view class="flex justify-between" style="border: #b5b1b1 1upx solid; height: 55upx; border-radius: 10upx; width: 500upx;margin-top: 10upx;">
									<input class="" placeholder="请输入验证码" name="input" style="text-align: left; text-indent: 55upx;">
									<image src="../../../static/input/图片验证码.png" class="solid-left" mode="" style="width: 120upx; height: 50upx;margin-right: 8upx;"></image>
									</input>
								</view>
							</view>

							<view>
								<button class="" style="margin: 45upx 0; background-color: #fe934c;color: #FFFFFF;height: 70upx; line-height: 70upx; width: 500upx;" form-type="submit">登&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;录</button>
							</view>
							<view class="flex justify-between" style="font-size: 26upx;">
								<view @tap="goMore('/pages/index/Personal-center/login')">注册新账号</view>
								<view @tap="goMore('/pages/index/Personal-center/forget-password')">忘记密码</view>
							</view>
						</view>
					</form>
					
					
					<view style="height: 40upx;"></view>
				</view>
			</view>
		</view>
		<view style="height: 100upx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="goMore('/pages/index/index')" data-cur="Home">
				<view class='cuIcon-cu-image'>
				<image :src="'../../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Call_me')" data-cur="报事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/消息' + [PageCur=='报事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='报事'?'text-red':'text-gray'">报事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Community_service')" data-cur="办事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/办事' + [PageCur=='办事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='办事'?'text-red':'text-gray'" >办事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_play/index_play')" data-cur="发现">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/发现' + [PageCur=='发现'?'_change':''] + '.png'" style="width: 43rpx; height: 38rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='发现'?'text-red':'text-gray'">发现</view>
			</view>
			<view class="action" @click="goMore('/pages/index/Personal-center/Personal-center')" data-cur="我的">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/我的' + [PageCur=='我的'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='我的'?'text-red':'text-gray'">我的</view>
			</view>
		</view>
	</view>
</template>

<script>
	import xflSelect from '../../../components/xfl-select/xfl-select.vue'
	var  graceChecker = require("../../../common/graceChecker.js");
	export default {
		data() {
			return {
				PageCur: '我的',
				TabCur: 0,
				scrollLeft: 0,
				imgList: [],
				switchA: false,
				switchB: true,
				switchC: false,
				switchD: false,
				radio: 'A',
				checkbox: [{
					value: 'A',
					checked: false
				}, {
					value: 'B',
					checked: true
				}, {
					value: 'C',
					checked: false
				}],
			
			}
		},
		components: { xflSelect },  //注册为子组件
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
			PickerChange(e) {
				this.index = e.detail.value
			},
			SwitchA(e) {
				this.switchA = e.detail.value
			},
			SwitchB(e) {
				this.switchB = e.detail.value
			},
			SwitchC(e) {
				this.switchC = e.detail.value
			},
			SwitchD(e) {
				this.switchD = e.detail.value
			},
			
			CheckboxChange(e) {
				var items = this.checkbox,
					values = e.detail.value;
				for (var i = 0, lenI = items.length; i < lenI; ++i) {
					items[i].checked = false;
					for (var j = 0, lenJ = values.length; j < lenJ; ++j) {
						if (items[i].value == values[j]) {
							items[i].checked = true;
							break
						}
					}
				}
			},
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
			    //定义表单规则
			    var rule = [
				    {name:"user", checkType : "string", checkRule:"1,8",  errorMsg:"用户名为必填项"},
					{name:"pass", checkType : "string", checkRule:"1,50",  errorMsg:"密码为必填项"},
					{name:"input", checkType : "string", checkRule:"1,50",  errorMsg:"验证码为必填项"},
			    ];
			    //进行表单检查
			    var formData = e.detail.value;
			    var checkRes = graceChecker.check(formData, rule);
			    if(checkRes){
			        uni.showToast({
						title:"验证通过!", 
					    icon:"none",
					});
					uni.navigateTo({
						url: "/pages/index/Personal-center/Personal-center"
					});
			    }else{
			        uni.showToast({ title: graceChecker.error, icon: "none" });
			    }
			},
		}
	}
</script>

<style>	
.img_1{
	position: absolute;
	left: 120upx;
	top: 60upx;
}
.img_2{
	position: absolute;
	right: 120upx;
	top: 60upx;
}
.uni-input{
	border-radius: 10upx;
	border: #b5b1b1 1upx solid;
	margin-top: 10upx;
	height: 60upx;
	width: 500upx;
	text-align: left;
	text-indent: 55upx;
}
.solid-bottom{
	padding: 15upx 20upx;
	margin: 0 auto;
}

.cu-btn {
	position: relative;
	display: inline-flex;
	align-items: center;
	justify-content: center;
	font-size: 24upx;
	height: 50upx;
	width: 140upx;
	line-height: 1;
	text-align: center;
	text-decoration: none;
	overflow: visible;
	margin-right: initial;
	border-left: #CCCCCC 1upx solid;
	padding: 0;
	margin: 0;
}

</style>
