<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action" @tap="goMore('/pages/index/index')">
					<text class="cuIcon-close"></text> 首页-社区商圈
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search">
				<view class="action" @tap="goMore('/pages/index/index')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					社区商圈
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../../static/input/社区商圈.png" style="width: 750rpx; height: 450rpx;" mode=""></image>
		</view>
		<view class="cu-bar bg-white solid-bottom line-gray">
			<view class="action">
				<image src="../../../static/model/图层18.png" mode="" style="width: 50upx; height: 40upx; padding-right: 10upx;"></image>
				<view class="text-red"><text style="color: #333333; font-size: 32rpx; font-weight: 590; padding-right: 10upx;">社区公告</text></view>
				<view class="text-xs text-black">廿四季节气——今日立冬</view>
			</view>
			<view class="action">
				<button class="cu-btn shadow"  @tap="goMore('/pages/index/index_people/Community_announcement')" data-target="gridModal">更多</button>
			</view>
		</view>
		<view class="cu-list grid bg-white" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList" @tap="gotoUrl(item)" :key="index" v-if="index<gridCol*2">
				<view :class="['icon-' + item.cuIcon,'text-' + item.color]" >
					 <view class="cu-tag badge" v-if="item.badge!=0" >
						<block v-if="item.badge!=1">{{item.badge>99?'99+':item.badge}}</block>
					</view> 
				</view>
				<text>{{item.name}}</text>
			</view>
			<view class="intro-all bg-white">
			    <view class="introduce">
				     模块简介：<br>
					 展示社区生活商圈，推荐特色品牌商家，颁布社区与商家合作活动以及商家自身活动
			    </view>
			</view>
		</view>
		
		<view class="bg-white" >
			<view class="bg-white" style="border-top: #DDDDDD 1upx solid;">
				<view style="padding: 15upx 20upx;">猜你喜欢</view>
				<view class="mall_contents bg-white flex justify-around" style="">
					<view>
						<image src="../../../static/input/社区商圈改_07.png" mode="" style=" padding: 5upx;width: 220upx;height: 160upx;"></image>
					</view>
					<view class="" style="line-height: 40upx; padding: 5upx;">
						<view class="text-black">
							宜宾市翠屏区众智种植养殖专业合作社
						</view>
						<view class="flex justify-between" style="font-size: 22upx;padding-top: 25upx;">
							<view>
								<image src="../../../static/input/社区商圈改_14.png" mode="" style="width: 32upx;height: 30upx;padding-right: 5upx;"></image>
								<image src="../../../static/input/社区商圈改_14.png" mode="" style="width: 30upx;height: 30upx;"></image>
							</view>
							<view><button class="shop-btn shadow" @tap="showModal" data-target="gridModal">门店自提</button></view>
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
				cuIconList: [{
				    cuIcon: 'ebe',
					badge: 0,
					name: '商圈地图',
					url: '/pages/index/index_shopping/Business_map',
				}, {
					cuIcon: 'ec',
					badge: 0,
					name: '品牌商家',
					url: '/pages/index/index_shopping/Brand_merchants',
				},
				{
					 cuIcon: 'e',
					badge: 0,
					name: '商家活动',
					url: '/pages/index/index_shopping/index_business',
				}],
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
.shop-btn{
	color: #FFFFFF;
	width: 100rpx; 
	background-color: #06c1ae;
	font-size: 20upx;
	padding: 0;
	margin: 0;
}
.intro-all {
	padding: 10upx 70upx;
}
.introduce{
	border:5rpx dashed #f0ad79;
	margin: 0 ;
	padding: 5upx;
	line-height: 38rpx;
	color: #fdcc6a;
	width: 600upx;
	text-align: left;
	font-size: 27upx;
}
.Illustration1{
	height: 400upx;
}
</style>
