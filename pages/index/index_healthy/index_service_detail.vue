<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action" @tap="goMore('/pages/index/index_healthy/index_healthy')">
					<text class="cuIcon-close" ></text> 健康驿站-卫生服务中心
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_healthy/index_services')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					详情
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="cu-list menu-avatar">
			<view class="bg-white solid-bottom ">
				<view class="" style="margin: 0 20upx ; padding-bottom: 10upx;">
					<view class="content">
						<view class="text-gray text-center" style="padding: 15upx 0;font-size: 31upx;">					
							<view class="text-center text-black">
								<text class="text-red text-xl">华大社区卫生服务中心</text>
							</view>
						</view>
						<view class="margin-top-sm flex justify-around align-center">
							<view class=" text-df">2019-12-12 16:00</view>
							<view style="font-size: 27upx;">卫生服务</view>
							<view class="action">
								<text class="">2404</text>
								<text class=""><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="service-intro">
			    <view class="text-red margin-left" style="font-size: 35upx;padding: 12upx 0;">服务中心简介:</view>
				<view class="padding-lr">
				 	<view class="txtmodle padding-lr bg-white">
				 		<view class="text-xs" style="height: 300upx; padding-top: 10upx;">
				 			<text class="">华大社区卫生服务中心位于</text>
				 		</view>
				 	</view>
				 	<view class="txtmodle padding-lr bg-white margin-top">
				 		<view class="padding-tb-sm text-xs">
				 			<text class="">电话：124393025</text>
							<image src="../../../static/input/电话.png" mode="" class="arrow"></image>
							<text class="text-red" style="float: right;">一键拨号</text>
				 		</view>
				 	</view>
				 	<view class="txtmodle padding-lr bg-white margin-top">
				 		<view class="padding-tb-sm text-xs">
				 			<text class="">详细地址：五粮液大道酒圣路8号</text>
				 			<image src="../../../static/input/椭圆10.png" mode="" class="arrow" style="width: 25upx; height: 40upx;" ></image>
				 			<text class="text-red" style="float: right;">一键查看</text>
				 		</view>
				 	</view>
					<view class="txtmodle padding-lr bg-white margin-top">
						<view class="padding-tb-sm text-xs">
							<text class="">公交路线：乘坐1、3路到宜宾学院下车</text>
						</view>
					</view>
					<view >
						<view style="height: 100upx;"></view>
					</view>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom line-gray">
			
		</view>
		
		<view style="height: 96rpx;"></view>
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
	background-color: #c9f5ff;
}

.txtmodle{
	border: #DDDDDD 2upx solid;
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
</style>
