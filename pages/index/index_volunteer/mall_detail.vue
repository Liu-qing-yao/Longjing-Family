<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_points-Mall')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					兑换详情
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class=" solid bg-white" style="margin: 30upx 30upx 15upx; border-radius: 15upx;">
			<view class="solid-bottom text-center">
				<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 45upx 15upx; width: 620upx;"></image>
			</view>
			<view class="solid-bottom" style="padding: 15upx 45upx;">
				<view class="text-red" style="font-size: 31upx; padding-bottom: 10upx;">商品名称：彩虹雨伞</view>
				<view style="font-size: 26upx;line-height: 45upx;">详情简介:光明社区与会超市推出积分换购活动，感恩回馈...</view>
			</view>
			<view class="flex justify-between solid-bottom text-red" style="padding: 15upx 45upx;font-size: 26upx;">
				<view style="padding-top: 10upx;">积分：<text style="font-size: 32upx;">299</text></view>
				<view style="padding-top: 10upx;">状态：未对换</view>
				<view>
					<button class="exchange bg-orange"  @tap="showModalS5" data-target="Modal" >积分兑换</button>
				</view>
			</view>
			<view style="padding: 15upx 45upx;font-size: 26upx;line-height: 45upx;">
				<view class="text-red"  style="font-size: 31upx; padding-bottom: 10upx;">阅读指南</view>
				<view>
					上门自提：光明社区与会超市xx年x月x活动时间内上午9点至晚上6点工作时间内自行前往领取。
				</view>
				<view>
					联系电话：1232435668
				</view>
				<view>详细地址：光明社区光明街道与会超市12号</view>
			</view>
		</view>
		
		<view class="cu-modal" :class="modalNameS5=='Modal'?'show':''">
			<view class="cu-dialog solid">
				<view class="cu-bar bg-white justify-start">
					<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
				</view>
				<view class="solid-top text-center" style="padding: 30upx;" >
					兑换成功！
				</view>
				<view class=""  @tap="hideModalS5" style="margin: 20upx 0 15upx 550upx;">
					<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
				</view>
			</view>
		</view>
		<view style="height: 80upx;"></view>
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
				modalNameS5: null,
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
			showModalS5(e) {
				this.modalNameS5 = e.currentTarget.dataset.target
			},
			hideModalS5(e) {
				this.modalNameS5 = null
			},
		}
	}
</script>

<style>
.exchange{
	height: 50upx;
	width: 120upx;
	line-height: 50upx;
	font-size: 22upx;padding: 0;
}
</style>
