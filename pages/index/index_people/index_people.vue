<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index')">
					<text class="cuIcon-close"></text> 关闭-龙井人家
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index')">
					<!-- <text class="cuIcon-homefill text-gray"></text> -->
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					民呼我应
				</view>
				<view class="action">
					<!-- <text class="cuIcon-recordfill text-red"></text> -->
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../../static/input/2.7.png" style="width: 750rpx; height: 350rpx;" mode=""></image>
		</view>
		<view class="cu-bar bg-gray solid-bottom line-gray solid-top">
			<view class="action">
				<image src="../../../static/model/图层18.png" mode="" style="width: 50upx; height: 40upx; padding-right: 10upx;"></image>
				<view class="text-red"><text style="color: #333333; font-size: 32rpx; font-weight: 590; padding-right: 10upx;">社区公告</text></view>
				<view class="text-xs text-black">廿四季节气——今日立冬</view>
			</view>
			<view class="action">
				<button class="cu-btn shadow" @tap="goMore('/pages/index/index_people/Community_announcement')" data-target="gridModal">更多</button>
			</view>
		</view>
		
		<view class="cu-list grid bg-white" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList" :key="index" @tap="gotoUrl(item)" v-if="index<gridCol*3">
				<view :class="['icon-' + item.cuIcon,'text-' + item.color]" >
					 <view class="cu-tag badge" v-if="item.badge!=0" >
						<block v-if="item.badge!=1">{{item.badge>99?'99+':item.badge}}</block>
					</view> 
				</view>
				<text>{{item.name}}</text>
			</view>
		</view>
		<view class="intro-all bg-white">
		    <view class="introduce">
			     模块简介：<br>
				 展示社区概况，显示相关政策和办事流程，响应社区居民反应问题，公式问题的具体解决情况，
				 接受居民对社区工作的建议。
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
				cuIconList: [{
				    cuIcon: 'eca',
					badge: 0,
					name: '政策发布',
					url: '/pages/index/index_people/Policy_release',
					
				}, {
					cuIcon: 'ebbc',
					badge: 0,
					name: '办事指南',
					url: '/pages/index/index_people/index_Guide',
				
				}, {
					 cuIcon: 'ebab',
					badge: 0,
					name: '三务公开',
					url: '/pages/index/index_people/Three_affairs',
					
				},
				{
					 cuIcon: 'ebae',
					badge: 0,
					name: '建言献策',
					url: '/pages/index/index_people/Advice',
				},
				{
					 cuIcon: 'ebfc',
					badge: 0,
					name: '你呼我应',
					url: '/pages/index/index_people/Call_me',
					
				},
				{
					 cuIcon: 'ebdfe',
					badge: 0,
					name: '民生实事',
					url: '/pages/index/index_people/People_livelihood',
					
				},
				{
					 cuIcon: 'ebedf',
					badge: 0,
					name: '社区公告',
					url: '/pages/index/index_people/Community_announcement',
					
				},
				{
					 cuIcon: 'ebcfdf',
					badge: 0,
					name: '线下服务站',
					url: '/pages/index/index_people/Community_service',

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
	padding: 30rpx 0;
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
