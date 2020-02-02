<template>
	<view>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的积分
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
					我的积分
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view >
				<view class="bg-white solid-bottom " style="padding: 15upx;" >
					<button class="bg-orange" style="border-radius: 300upx; width: 200upx; height: 200upx;padding: 0;">
						<view class="text-white" style="font-size: 70upx;padding: 0;">58</view>
					    <view class="text-white" style="font-size: 28upx; position: absolute; top: 110upx; left: 70upx;padding: 0;">积分</view>
					</button>
				</view>
			</view>
			
		</view>
		<view class="bg-white text-orange padding-top padding-lr-sm" style="padding-bottom: 15upx; font-size: 32upx;">已兑换商品</view>
		<view class="flex justify-around bg-white" >
			<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
				<view>
					<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
				</view>
				<view class="" style="line-height: 35upx; padding: 5upx;">
					<view class="text-red">商品名称</view>
					<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
					<view class="" style="font-size: 18upx;">积分：200</view>
					<view class="" style="font-size: 18upx;">状态：已兑换</view>
					<button class="shadow bg-orange"  style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">兑换成功</button>
				</view>
			</view>
			<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
				<view>
					<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
				</view>
				<view class="" style="line-height: 35upx; padding: 5upx;">
					<view class="text-red">商品名称</view>
					<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
					<view class="" style="font-size: 18upx;">积分：200</view>
					<view class="" style="font-size: 18upx;">状态：已兑换</view>
					<button class="shadow bg-orange"  style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">兑换成功</button>
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

</style>
