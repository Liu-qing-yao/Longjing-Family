<template>
	<view class="bg-white">
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 党建联盟-党组织简介
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/index_longjing/community-par-building1')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					区域党建
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav align-center solid-bottom">
			<view class="cu-item service-nav_1" :class="0==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_longjing/Grid_par_building')" data-id="0">
				<text class="" >网格党建</text>
			</view>
			<view class="cu-item service-nav_1" :class="1==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_longjing/community-par-building1')" data-id="1">
				<text>小区党建</text>
			</view>
		</scroll-view>
		<view class="flex bg-white solid-bottom" >
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/形状559.png" mode="" style="width: 30upx;height: 30upx; padding: 0; margin-right: 12upx;"></image>
				<view>请选择分类</view>
			</view>
			<view class="mall_change img-align" >
				先选择小区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker img-align">
						<image src="../../../static/input/下.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
			<view class="solid-right" >
			</view>

		</view>
		<view class="cu-list menu-avatar bg-white">
			<view class="Service_N">
				<view class="solid-bottom" style="margin: 20upx; padding-bottom: 10upx; ">
					<view class="content">
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
							<view class="text-center margin-lr text-black">葡萄园社区进行清洁卫生整改</view>
						</view>
						<view class="padding-lr">
							<view class="flex" style="border-left: #f8404c 2upx solid;padding: 0 25upx;">
								<image src="../../../static/input/益路有你_09.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
							</view>
						</view>
						<view class="margin-top-sm flex justify-between">
							<view class="text-gray text-df">2020</view>
							<view class="action">
								<text class="text-gray">2404</text>
								<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
				<view class=" solid-bottom" style="margin: 20upx;padding-bottom: 10upx;">
					<view class="content">
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
							<view class="text-center margin-lr text-black">金象社区进行居民工作满意调查</view>
						</view>
						<view class="padding-lr">
							<view class="flex" style="border-left: #f8404c 2upx solid;padding: 0 25upx;">
								<image src="../../../static/input/益路有你_11.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
							</view>
						</view>
						<view class="margin-top-sm flex justify-between">
							<view class="text-gray text-df">2020</view>
							<view class="action">
								<text class="text-gray">2404</text>
								<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view style="height: 96rpx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot solid-top">
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
				Tab: 1,
				botton: 0,
				scrollLeft: 0,
				scroll: 0,
				index_Street: -1,
				index_Communities: -1,
				picker1: ['华大小区', '大楻桶小区', '广华小区','红苕地小区'],
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
page {
			background-color: #FFFFFF;
		}

.party_cont{
	padding: 20upx 0 0 20upx;
	font-size: 25upx;
}
.txtmodle{
	border: #fd3838 2upx solid;
}
.cu-btn1 {
	color: #333333;
	width: 150rpx; 
	background-color: #f0ad79;
	position: relative;
	border: 0upx;
	display: inline-flex;
	align-items: center;
	justify-content: center;
	box-sizing: border-box;
	padding: 0 30upx;
	font-size: 28upx;
	height: 64upx;
	line-height: 1;
	text-align: center;
	text-decoration: none;
	overflow: visible;
	margin-left: initial;
	transform: translate(0upx, 0upx);
	margin-right: initial;
}
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 15upx 5upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 220upx;
		text-align: center;
	}
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
}
.service-title{
	position: absolute;
	margin: 0;
	left: 250upx;
	color: red;
	font-size: 30upx;
}
.logo-list{
	width: 40upx;
	height: 30upx;
	margin: 10upx;
}
.count-logo{
	width: 45upx;
	height: 20upx;
	margin: 0 5upx;
}
.text-grey{
	position: absolute;
	right: 25upx;
	bottom: 10upx;
}
.zuo{
	width: 700upx;
}

.cu-list.menu-avatar>.pic-modle{
	height: 210upx;
}
.cu-list.menu-avatar>.cu-item .content>view{
	text-align: center;
} 

.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
.service-intro{
	background-color: #FFFFFF;
}

.txtmodle{
	border: #fd3838 2upx solid;
}
.party_cont{
	padding: 20upx 0 0 20upx;
	font-size: 25upx;
}
.arrow{
	width: 34upx;
	height: 34upx;
	position: absolute;
	right: 180upx;
}
.service-action{
	display: flex;
	justify-content: space-between;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	padding: 0 10upx;
	display: flex;
	justify-content: space-between;
}
.service-nav_1{
		/* background: #5ddad4; */
		margin: 10upx 0 10upx 8upx;
		border-radius: 15upx;
		width: 190upx;
		height: 80upx;
		line-height: 80upx;
		padding: 0;
		text-align: center;
		border: #DDDDDD 1upx solid;
	}
.mall_change{
	border-left: #DDDDDD 1upx solid;
	border-right: #DDDDDD 1upx solid;
	padding: 10upx 27upx;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 28upx;
}
</style>
