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
		
		 <scroll-view scroll-x class="bg-white nav navfirst align-center solid-bottom">
		 	<view class="cu-item par_nav_1" :class="0==TabCur?'bg-orange':'bg-gray'" @tap="goMore('/pages/index/Personal-center/Participation')" data-id="0">
		 		<text class=""></text>志 愿 活 动
		 	</view>
		 	<view class="cu-item par_nav_1" :class="1==TabCur?'bg-orange cur':'bg-gray'" @tap="goMore('/pages/index/Personal-center/Participation1')" data-id="1">
		 		<text class=""></text>生 活 动 态
		 	</view>
		 </scroll-view>
		 <!-- <scroll-view scroll-x class="bg-white nav navfirst align-center solid-bottom">
		 	<view class="cu-item par_nav_2" :class="0==Tab?'bg-orange':'bg-gray'" @tap="goMore('/pages/index/Personal-center/Participation2')" data-id="0">
		 		<text class=""></text>我 的 消 息
		 	</view>
		 	<view class="cu-item par_nav_2" :class="1==Tab?'bg-orange cur':'bg-gray'" @tap="goMore('/pages/index/Personal-center/Participation1')" data-id="1">
		 		<text class=""></text>我 的 动 态
		 	</view>
		 </scroll-view> -->
		 <view class="bg-white solid-bottom" style="padding: 25upx 15upx;">
		 	    <view class="flex justify-between">
		 	    	<view class="flex justify-left">
		 	    		<view class="face"><image src="../../../static/input/人.png" mode="" style="width: 100upx; height: 100upx;"></image></view>
		 	    		<view class="padding-left">
		 	    			<view>李明明</view>
		 	    			<view style="padding-top: 15upx; font-size: 24upx;">2019-12-12 22：00</view>
		 	    	    </view>
		 	    	</view>
		 	    	<image src="../../../static/input/删除.png" mode="" style="width: 27upx; height: 32upx;"></image>
		 	    </view>
		 		<view>今天进行了社区展开法制教育，很有收获哦</view>
				<view>
					<image src="../../../static/input/图层860.png" mode="" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"></image>
					<image src="../../../static/input/图层860.png" mode="" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"></image>
				</view>
		 		<view class="flex justify-end ">
		 			<view class="padding-lr">
		 				<image src="../../../static/input/爱心.png" mode="" style="width: 38upx; height: 30upx; padding-right: 5upx;"></image>
		 				赞
		 			</view>
		 			<view>
		 				<image src="../../../static/input/评论.png" mode="" style="width: 38upx; height: 30upx; padding-right: 5upx;"></image>
		 				评论
		 			</view>
		 		</view>
		 </view>
		 <view class="bg-white solid-bottom" style="padding: 25upx 15upx;">
				<view class="flex justify-between">
					<view class="flex justify-left">
						<view class="face"><image src="../../../static/input/人.png" mode="" style="width: 100upx; height: 100upx;"></image></view>
						<view class="padding-left">
							<view>李明明</view>
							<view style="padding-top: 15upx; font-size: 24upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<image src="../../../static/input/删除.png" mode="" style="width: 27upx; height: 32upx;"></image>
				</view>
		 		<view>今天进行了社区展开法制教育，很有收获哦</view>
		 				<view>
		 					<image src="../../../static/input/图层860.png" mode="" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"></image>
		 					<image src="../../../static/input/图层860.png" mode="" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"></image>
		 				</view>
		 		<view class="flex justify-end ">
		 			<view class="padding-lr">
		 				<image src="../../../static/input/爱心.png" mode="" style="width: 38upx; height: 30upx; padding-right: 5upx;"></image>
		 				赞
		 			</view>
		 			<view>
		 				<image src="../../../static/input/评论.png" mode="" style="width: 38upx; height: 30upx; padding-right: 5upx;"></image>
		 				评论
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
				TabCur: 1,
				Tab: 1,
				botton: 0,
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
.par_nav_2{
	width: 188upx;
	text-align: center;
	margin: 5upx 0 0;
	padding: 0;
	color: #ffffff;
	float: right;
}	
.face image{
	flex-shrink:0;width:15vw;height:15vw;
	width:100%;height:100%;border-radius:100%
		}
</style>
