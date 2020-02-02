<template>
	<view>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的消息
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					我的消息
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face"><image src="../../../static/input/2.7.png" mode="" style="width: 120upx; height: 100upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">张三（书记）<image src="../../../static/input/删除.png" mode="" style="width: 27upx; height: 32upx;"></image></view>
							<view style="font-size: 24upx;">点赞<image src="../../../static/input/爱心.png" mode="" style="width: 34upx; height: 25upx; margin: 5upx 5upx 0;"></image></view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
						<view>
							<image src="../../../static/input/图层860.png" mode="" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"></image>
						</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face"><image src="../../../static/input/2.7.png" mode="" style="width: 120upx; height: 100upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">张三（书记）<image src="../../../static/input/删除.png" mode="" style="width: 27upx; height: 32upx;"></image></view>
							<view style="font-size: 24upx;">评论：新年快乐！</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view>
						<image src="../../../static/input/图层860.png" mode="" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"></image>
					</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face"><image src="../../../static/input/2.7.png" mode="" style="width: 120upx; height: 100upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">张三（书记）<image src="../../../static/input/删除.png" mode="" style="width: 27upx; height: 32upx;"></image></view>
							<view style="font-size: 24upx;">评论：辛苦了！</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view>
						<image src="../../../static/input/图层860.png" mode="" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"></image>
					</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">阳光社区a栋居民养狗噪音扰民</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="action" style="font-size: 24upx;">
						<image src="../../../static/input/形状599拷贝@3x.png" mode="" style="width: 25upx;height: 25upx;"></image>
						<text class="text-orange">您的报事未受理</text>
					</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">芜湖社区c栋楼灯损坏</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="action" style="font-size: 24upx;">
						<image src="../../../static/input/形状616@3x.png" mode="" style="width: 40upx;height: 30upx; margin: 0 10upx;"></image>
						<text class="text-blue">正在办理</text>
					</view>
			</view>
			<view class="bg-white solid-bottom solid-top flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">芜湖社区c栋楼灯损坏</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="action" style="font-size: 24upx;">
						<image src="../../../static/input/形状13拷贝2@3x.png" mode="" style="width: 30upx;height: 30upx; margin: 0 10upx;"></image>
						<text class="text-red">您的报事已完结</text>
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
				
			}
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
.cu-list.menu-avatar>.cu-item .content {
	position: absolute;
	left: 200upx;
	line-height: 1.6em;
}
</style>
