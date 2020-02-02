<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 我的
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<!-- <view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_volunteer')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					注册志愿者
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view> -->
		</view>
		<view class="bg-white" style="height: 60upx;"></view>
		<view class="bg-white">
			<view class="padding ">
				<view class="padding-lr bg-white" style="border: #555555 1upx solid; border-radius: 15upx;">
					<view class="vol_img">
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_1" style="width: 50upx; height: 80upx;"></image>
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_2" style="width: 50upx; height: 80upx;"></image>
					</view>
					<view class="text-center margin-top">
						<text class="text-xl text-black ">注册</text>
					</view>
					<view class="" style="margin: 10upx 60upx;">
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left">用户名</text>
								<text class="text-left text-red" style="font-size: 60upx;">*</text>
							</view>
							<input class="uni-input" focus />
						</view>
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left" style="padding-right: 10upx;">街道</text>
								<image src="../../../static/input/三角.png" mode="" style="width: 30upx; height: 28upx;"></image>
							</view>
							<input class="uni-input" focus password type="text"/>
						</view>
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left" style="padding-right: 10upx;">社区</text>
								<image src="../../../static/input/三角.png" mode="" style="width: 30upx; height: 28upx;"></image>
							</view>
							<input class="uni-input" focus password type="text" />
						</view>
						
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left">真实姓名</text>
								<text class="text-left text-red" style="font-size: 60upx;">*</text>
							</view>
							<input class="uni-input" focus />
						</view>
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left">电话号码</text>
								<text class="text-left text-red" style="font-size: 60upx;">*</text>
							</view>
							<input class="uni-input" focus placeholder="请输入手机号"/>
						</view>
						<view class="padding-top">
							<view class="flex" style="height: 40upx;">
								<text class="text-left">验证码</text>
								<text class="text-left text-red" style="font-size: 60upx;">*</text>
							</view>
							<view class="solid flex justify-between" style="height: 55upx; border-radius: 20upx; width: 500upx;margin-top: 10upx;">
								<input placeholder="请输入验证码" name="input" style="text-align: center;">
								<button class='cu-btn bg-white text-red' >获取验证码</button>
								</input>
								
							</view>
						</view>
						<view class="padding-top padding-bottom-xl">
							<view class="flex" style="height: 40upx;">
								<text class="text-left">电子邮箱</text>
							</view>
							<input class="uni-input" focus type="idcard"/>
						</view>
						<view class="flex justify-between">
							<view class="text-red">(加*为必填项)</view>
						</view>
						
						<view>
							<button class="bg-orange margin">注&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;册</button>
						</view>
					</view>
					
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
	export default {
		data() {
			return {
				PageCur: 'Home',
				TabCur: 0,
				scrollLeft: 0,
			
			}
		},
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
		}
	}
</script>

<style>	
.img_1{
	position: absolute;
	left: 120upx;
	top: 160upx;
}
.img_2{
	position: absolute;
	right: 120upx;
	top: 160upx;
}
.uni-input{
	border-radius: 10upx;
	border: #b5b1b1 1upx solid;
	margin-top: 10upx;
	height: 50upx;
	width: 500upx;
	text-align: center;
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
