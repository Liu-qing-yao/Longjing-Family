<template>
	<view>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					我的收藏
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		 
		 <view class="cu-list menu-avatar">
		 	<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
		 		<view class="flex" @tap="goMore('/pages/index/index_longjing/com-style-detail')">
		 			<view>
		 				<image src="../../../static/input/益路有你_11.png" mode="" style="width: 200upx; height: 160upx;"></image>
		 			</view>
		 			<view class="" style="margin-left: 15upx;">
		 				<view class="text-black">法制宣传进社区</view>
		 				<view class="text-gray text-sm flex">
		 					<view class="text-cut" style="padding-top: 90upx;">
		 						<text class=" text-red  margin-right-xs"></text>
		 						2019-12-22  16:00
		 					</view> 
		 				</view>
		 			</view>
		 		</view>
		 		
		 	</view>
		 	<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
		 		<view class="flex" @tap="goMore('/pages/index/index_longjing/com-style-detail')">
		 			<view>
		 				<image src="../../../static/input/益路有你_11.png" mode="" style="width: 200upx; height: 160upx;"></image>
		 			</view>
		 			<view class="" style="margin-left: 15upx;">
		 				<view class="text-black">葡萄园社区开发创文</view>
		 				<view class="text-gray text-sm flex">
		 					<view class="text-cut" style="padding-top: 90upx;">
		 						<text class=" text-red  margin-right-xs"></text>
		 						2019-12-22  16:00
		 					</view> 
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
				PageCur: '我的',
			};
		},
		
		methods: {
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
		}
	}
</script>

<style>
	
</style>
