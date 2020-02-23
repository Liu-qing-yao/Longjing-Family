<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search">
				<view class="action" @tap="goMore('/pages/index/index')">
					
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					益路有你
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../../static/input/volunteer.png" style="width: 750rpx; height: 400rpx;" mode=""></image>
		</view>
		<view class="bg-gray solid-bottom solid-top flex justify-between" style="margin: 0;height: 80upx;line-height: 60upx; padding-top: 10upx;">
			<view class=" flex justify-left img-align">
				<view class="text-red img-align margin-left">
					<image src="../../../static/model/图层18.png" mode="" style="width: 50upx; height: 40upx; padding-right: 10upx;"></image>
					<text style="color: #333333; font-size: 32rpx; font-weight: 590; padding-right: 10upx;">社区公告</text>
				</view>
				<view class="text-xs text-black">廿四季节气——今日立冬</view>
			</view>
			<view class="">
				<button class="cu-btn1"  @tap="goMore('/pages/index/index_people/Community_announcement')" data-target="gridModal" style="color: #333333;">更多</button>
			</view>
		</view>
		<view class="cu-list grid bg-white" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList"  @tap="gotoUrl(item)" :key="index" v-if="index<gridCol*2">
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
					 注册成为志愿者，查询志愿服务需要，在线报名参与志愿活动；各单位在线发布公益活动公告，承担社会责任。
			    </view>
			</view>
		</view>
		
		<view class="bg-white padding-top">
			<image src="../../../static/input/volunteer_29.png" mode="" style="width: 750rpx; height: 220rpx;"></image>
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
				    cuIcon: 'efc',
					badge: 0,
					name: '志愿服务',
					url: '/pages/index/index_volunteer/index_volService',
				},{
					 cuIcon: 'ea',
					badge: 0,
					name: '光荣榜',
					url: '/pages/index/index_volunteer/honor_List',
				},
				{
					 cuIcon: 'ecabdd',
					badge: 0,
					name: '积分兑换',
					url: '/pages/index/index_volunteer/index_points-Mall',
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
.intro-all {
	padding: 10upx 80upx;
}
.introduce{
	border:5rpx dashed #f0ad79;
	margin: 0 ;
	padding: 5rpx;
	line-height: 38rpx;
	color: #fdcc6a;
	width: 600upx;
	text-align: left;
	font-size: 27upx;
}
.Illustration1{
	height: 400upx;
}
.img-align *{
		display: inline-block;
		vertical-align: middle;
		font-size: 28upx;
	}
</style>

