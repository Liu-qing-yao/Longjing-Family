<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 建言献策-我的建言献策
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_people/Advice')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					建言献策
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<view class="flex justify-between bg-white padding">
			<view class="flex">
				<image src="../../../static/input/背景拷贝.png" mode="" style="width: 60upx; height: 40upx; padding-right: 10upx;"></image>
				<view class="text-black text-xl">我的建言献策</view>
			</view>
		</view>
		
		<view class="cu-list menu-avatar margin-tb-sm">
			<view class="bg-white" style="padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="content">
					<view class="text-gray" style="padding: 15upx;">
						<view class="text-black text-s">社区卫生需要好好整治</view>

					</view>
					<view class="margin-top-sm flex justify-between">
						<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
						<view class="action">
							<text class="text-xs">2404</text>
							<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
				</view>
			</view>
			<view class="bg-white" style="padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="content">
					<view class="text-gray" style="padding: 15upx;">
						<view class="text-black text-s">楼道灯光时好时坏，希望领导好好检查</view>
					</view>
					<view class="margin-top-sm flex justify-between">
						<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
						<view class="action">
							<text class="text-xs">2404</text>
							<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
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
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
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
	
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	text-align: center;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 15upx 6upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 175upx;
		text-align: center;
		padding: 0;
		height: 85upx;
	}
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
	 
}
.cu-btn{
	padding: 0; margin: 0;
}
.adv_bnt{
padding: 20upx 0;
text-align: center;
}
.logo-list{
	width: 40upx;
	height: 30upx;
	margin: 10upx;
}
.count-logo{
	width: 40upx;
	height: 20upx;
	margin: 0 5upx;
}

.com_count{
	padding-top: 130upx;
}
.zuo{
	width: 700upx;
}

.cu-list.menu-avatar>.pic-modle{
	height: 210upx;
}
.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}

.txtmodle{
	border: #7B7B7B 2upx solid;
	border-radius: 10upx;
}
</style>
