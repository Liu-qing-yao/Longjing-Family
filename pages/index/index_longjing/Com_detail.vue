<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/Com_overview')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					详情
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<view class="cu-list menu-avatar">
			<view class="bg-white solid-bottom ">
				<view class="" style="margin: 0 20upx ; padding-bottom: 10upx;">
					<view class="content">
						<view class="text-gray text-center" style="padding: 15upx 0;font-size: 34upx; margin: 0 140upx;">					
							<view class="text-center text-red">华大社区</view>
						</view>
						<view class="margin-top-sm flex justify-around align-center">
							<view class=" text-df">2019-12-12 16:00</view>
							<view style="font-size: 27upx;">社区信息</view>
							<view class="action">
								<text class="">2404</text>
								<text class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="service-intro">
			    <view class="text-red margin-left" style="font-size: 35upx;padding: 12upx 0;">社区简介:</view>
				<view class="padding-lr">
				 	<view class="txtmodle padding-lr bg-white">
				 		<view class="text-xs" style="height: 300upx; padding-top: 10upx;">
				 			<text class="">华大街区...</text>
				 		</view>
				 	</view>
				 	<view class="txtmodle padding-lr bg-white margin-top">
				 		<view class="padding-tb text-xs">
				 			<text class="">电话：124393025</text>
							<image src="../../../static/input/电话.png" mode="" class="arrow"></image>
							<text class="text-red" style="float: right;">一键拨号</text>
				 		</view>
				 	</view>
				 	<view class="txtmodle padding-lr bg-white margin-top">
				 		<view class="padding-tb text-xs">
				 			<text class="">详细地址：五粮液大道酒圣路8号</text>
				 			<image src="../../../static/input/椭圆10.png" mode="" class="arrow" style="width: 25upx; height: 40upx;" ></image>
				 			<text class="text-red" style="float: right;">一键查看</text>
				 		</view>
				 	</view>
					<view class="txtmodle padding-lr bg-white margin-top">
						<view class="padding-tb text-xs">
							<text class="">公交路线：乘坐1、3路到宜宾学院下车</text>
						</view>
					</view>
				</view>
				<view class="text-red margin-left" style="font-size: 35upx;padding: 12upx 0;">社区班子成员:</view>
				<view class="padding-lr padding-bottom-xl">
				 	<view class="txtmodle bg-white flex" style="padding: 20upx 0 0 20upx;">
						<view ><image src="../../../static/input/人.png" mode="" style="width: 180upx;height: 180upx;"></image></view>
				 		<view class="text-xs " style="height: 200upx; padding-left: 25upx; line-height: 38upx;">
				 			<text class="">姓名：</text><br>
							<text class="">职务：</text><br>
				 		</view>
				 	</view>
				</view>
			</view>
		</view>
		<view class="bg-white text-red" style="border: #DDDDDD 1upx solid;padding: 15upx 0; font-size: 34upx;">
			<view class="action text-right padding-lr">
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
			</view>
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
		},
		
	}
</script>

<style>
.cu-btn{
		color: #333333; 
		width: 150rpx; 
		background-color: #f0ad79;
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
	border: #7b7b7b 2upx solid;
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
