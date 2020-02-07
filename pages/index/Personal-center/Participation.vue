<template>
	<view>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的参与
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					我的参与
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		 <scroll-view scroll-x class="bg-white nav navfirst align-center">
		 	<view class="cu-item par_nav_1" :class="0==TabCur?'bg-orange':'bg-gray'"  @tap="goMore('/pages/index/Personal-center/Participation')" data-id="0">
		 		<text class=""></text>志 愿 活 动
		 	</view>
		 	<view class="cu-item par_nav_1" :class="1==TabCur?'bg-orange cur':'bg-gray'" @tap="goMore('/pages/index/Personal-center/Participation1')" data-id="1">
		 		<text class=""></text>生 活 动 态
		 	</view>
		 </scroll-view>
		 <view class="cu-list menu-avatar bg-white">
		 	<view class=""> 
		 		<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
		 			<view class="content">
		 				<view class="text-gray flex" style=" font-size: 34upx;">
		 					<view class="text-red">宜宾市第二医院志愿者招募</view>
		 				</view>
		 				<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
		 					<view>
		 						<view class="">
		 						     需要人数：10人
		 						</view>
		 						<view class="">
		 						      开始时间：2019-12-22 16:00
		 						</view>
		 						<view class="">
		 						    结束时间：无
		 						</view>
		 					</view>
		 					<view>
		 						<button class="bg-orange flex" style="width: 180upx; height: 80upx;">
		 							<view class="text-center" style="padding-left: 10upx;">进行中</view>
		 						</button>
		 					</view>
		 				</view>
		 			</view>
		 		</view>
				
		 		<view class="" style="margin: 20upx 20upx 0; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
		 			<view class="content">
		 				<view class="text-gray flex" style=" font-size: 34upx;">
		 					<view class="text-red">宜宾市第二医院志愿者招募</view>
		 				</view>
		 				<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
		 					<view>
		 						<view class="">
		 						     需要人数：10人
		 						</view>
		 						<view class="">
		 						      开始时间：2019-12-22 16:00
		 						</view>
		 						<view class="">
		 						    结束时间：无
		 						</view>
		 					</view>
		 					<view style="">
		 						<button class="bg-gray flex" style="padding: 0 15upx; width: 180upx; height: 80upx;">
		 							<view class="text-center"><image src="../../../static/input/形状13.png" mode="" style="width: 45upx; height: 35upx;padding-right: 8upx;"></image></view>
		 							<view class="text-center text-white">已完成</view>
		 						</button>
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
				TabCur: 0,
				scrollLeft: 0,
			};
		},
		
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			Select(e) {
				this.Tab = e.currentTarget.dataset.id;
				this.scroll = (e.currentTarget.dataset.id - 1) * 60
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
.par_nav_1{
	width: 375upx;
	text-align: center;
	margin: 0;
	padding: 0;
	color: #ffffff;
}	
</style>
