<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index')">
					<text class="cuIcon-close"></text> 首页-玩味生活
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					玩味生活
				</view>
				<view class="action">
					<!-- <text class="cuIcon-recordfill text-red"></text> -->
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../../static/input/访问数222人.png" style="width: 750rpx; height: 350rpx;" mode=""></image>
		</view>
		<view class="intro-all bg-white" >
			<view class="flex justify-between solid" style="padding: 15upx;">
				<view class="bg-white" style="padding: 5upx 45upx">
					我要发布动态
				</view>
				<view class="margin-lr">
					<image src="../../../static/input/形状1.png" mode="" @tap="goMore('/pages/index/index_play/index_story')" style="width: 36upx; height: 36upx;"></image>
				</view>
			</view>
		   
		   <view class="text-orange" style="padding: 15upx 60upx; font-size: 33upx;">
		   	热门动态
		   </view>
		   <view class="bg-white solid" style="border-radius: 25upx; padding: 15upx 20upx; margin: 0 60upx;">
		   	    <view class="flex justify-left">
					<view><image src="../../../static/input/头像.png" mode="" style="width: 100upx; height: 100upx;"></image></view>
					<view class="padding-left">
					    <view>张三(社区书记)</view>
					    <view style="padding-top: 15upx; font-size: 24upx;">2019-12-12 22：00</view>
					</view>
				</view>
				
				<view>今天进行了社区整改，大家辛苦了...</view>
				<view class="flex justify-end padding-top-xl">
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
		   <view class="bg-white solid" style="border-radius: 25upx; padding: 30upx 20upx; margin: 30upx 60upx 0;">
		   	    <view class="flex justify-left">
		   			<view><image src="../../../static/input/头像.png" mode="" style="width: 100upx; height: 100upx;"></image></view>
		   			<view class="padding-left">
		   				<view>李四</view>
		   				<view style="padding-top: 15upx; font-size: 24upx;">2019-12-12 22：00</view>
		   			</view>
		   		</view>
		   				
		   		<view>今天进行了法制教育，很有收获哦！</view>
				
		   		<view class="flex justify-end padding-top-xl">
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
		</view>
		<view class="cu-bar bg-white">
			<view class="action">
			</view>
			<view class="action">
				<button class="cu-btn shadow" @tap="showModal" data-target="gridModal">更 多</button>
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
				PageCur: '发现',
				modalName: null,
				gridCol: 3,
				gridBorder: false,
				menuBorder: false,
				menuArrow: false,
				menuCard: false,
				skin: false,
				listTouchStart: 0,
				listTouchDirection: null
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

.cu-btn{
	color: #333333; 
	width: 150rpx; 
	background-color: #f0ad79;
}
.intro-all {
	padding: 0 0 30rpx;
}
.introduce{
	border:5rpx dashed #f0ad79;
	margin: 0 45rpx 0 45rpx;
	padding: 10rpx 10rpx;
	line-height: 48rpx;
	color: #fdcc6a;
	font-size: 27upx;
}
.Illustration1{
	height: 350upx;
}
</style>
