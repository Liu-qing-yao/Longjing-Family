<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_volunteer')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					志愿服务
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav navfirst align-center solid-top">
			<view class="cu-item service-nav_1" :class="0==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_volunteer/index_volService')" data-id="0">
				<text class="" >志愿服务</text>
			</view>
			<view class="cu-item service-nav_1" :class="2==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_volunteer/honor_List')" data-id="1">
				<text class="">光荣榜</text>
			</view>
			<view class="cu-item service-nav_1" :class="3==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_volunteer/index_points-Mall')" data-id="2">
				<text>积分兑换</text>
			</view>
		</scroll-view>
		
		<scroll-view scroll-x class="bg-white nav" style="text-align: center; border-bottom: #DDDDDD 2upx solid;">
			<view class="flex text-center">
				<view class="cu-item flex-sub" :class="index==TabCur?'text-red cur':''" v-for="(item,index) in List" :key="index" @tap="gotoUrl(item)" :data-id="index">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar bg-white">
			<view class="Service_N">
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content" @tap="goMore('/pages/index/index_volunteer/volunteer_news_detail')">
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
							<view class="text-center margin-lr text-black">创建全国文明城市：不断完善基础设施</view>
						</view>
						<view class="padding-lr">
							<view class="flex justify-around" style="border-left: #f8404c 2upx solid;padding: 0 25upx;">
								<image src="../../../static/input/益路有你_09.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
								<image src="../../../static/input/益路有你_11.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
								<image src="../../../static/input/益路有你_13.png" mode="" style="width: 280upx;height: 200upx;"></image>
							</view>
						</view>
						<view class="margin-top-sm flex justify-between">
							<view class="text-gray text-df">2020</view>
							<view class="action">
								<text class="text-gray">2404</text>
								<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx;padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content" @tap="goMore('/pages/index/index_volunteer/volunteer_news_detail')" >
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
							<view class="text-center margin-lr text-black">创建全国文明城市：不断完善基础设施</view>
						</view>
						<view class="padding-lr">
							<view class="flex justify-around" style="border-left: #f8404c 2upx solid;padding: 0 25upx;">
								<image src="../../../static/input/益路有你_09.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
								<image src="../../../static/input/益路有你_11.png" mode="" style="width: 280upx;height: 200upx; padding-right: 10upx;"></image>
								<image src="../../../static/input/益路有你_13.png" mode="" style="width: 280upx;height: 200upx;"></image>
							</view>
						</view>
						<view class="margin-top-sm flex justify-between">
							<view class="text-gray text-df">2020</view>
							<view class="action">
								<text class="text-gray">2404</text>
								<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx;">
					<view class="content">
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
						</view>
						<view class="" style="padding-left: 35upx;">
							<view class="" style="border-left: #f8404c 2upx solid;padding: 0 0 0 0; line-height: 60upx;">
								<view class="flex justify-between" @tap="goMore('/pages/index/index_volunteer/volunteer_news_detail')" style="padding-left: 20upx;">
									振兴社区开展志愿者活动
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
									</view>
								</view>
								<view class="flex justify-between"  @tap="goMore('/pages/index/index_volunteer/volunteer_news_detail')" style="padding-left: 20upx;">
									快来了解这些文明小知识吧！
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
									</view>
								</view>
								<view class="flex justify-between"  @tap="goMore('/pages/index/index_volunteer/volunteer_news_detail')" style="padding-left: 20upx;">
									夜晚开展志愿入户宣传
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
									</view>
								</view>
							</view>
						</view>
						<view class="margin-top-sm flex justify-between">
							<view class="text-gray text-df">2020</view>
						</view>
					</view>
				</view>
			
			</view>
			
			<view class="cu-bar solid-bottom line-gray" style="background-color: #d9d9d9;">
				<view class="text-black margin-left" >
					智慧龙井 发现您身边的天使
				</view>
				<!-- <view class="action">
					<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
				</view> -->
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
				TabCur: 2,
				Tab: 0,
				botton: 0,
				scrollLeft: 0,
				scroll: 0,
				List: [{
					name: '我要成为志愿者',
					url: '/pages/index/index_volunteer/registered_volunteers',
				}, 
				{
					name: '志愿活动',
					url: '/pages/index/index_volunteer/index_activities',
				},
				{
					name: '志愿新闻'
				}]
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
.cu-btn{
	color: #333333; 
	width: 150rpx; 
	background-color: #f0ad79;
}	
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.service-nav{
	border-bottom: 1upx #DDDDDD solid;
	/* display: flex;
	justify-content: center; */
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	padding: 0 10upx;
	display: flex;
	justify-content: space-between;
}
.service-nav_1{
		/* background: #5ddad4; */
		margin: 10upx 5upx;
		border-radius: 15upx;
		width: 170upx;
		height: 80upx;
		padding: 0;
		text-align: center;
		border: #DDDDDD 1upx solid;
		line-height: 80upx;
	}

.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
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
.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
.vol-news{
	border-left: #333333 1upx solid;
}
</style>
