<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 健康驿站-卫生服务中心
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_healthy/index_healthy')">
					<!-- <text class="cuIcon-homefill text-gray"></text> -->
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					卫生服务中心
				</view>
				<view class="action">
					<!-- <text class="cuIcon-recordfill text-red"></text> -->
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<scroll-view scroll-x class="bg-white nav navfirst align-center">
			<view class="cu-item service-nav_1" :class="0==Tab?'bg-orange cur':'bg-cyan'" @tap="goMore('/pages/index/index_healthy/index_common')" data-id="0">
				<text class="" >健康常识</text>
			</view>
			<view class="cu-item service-nav_1" :class="1==Tab?'bg-orange cur':'bg-cyan'" @tap="goMore('/pages/index/index_healthy/index_register')" data-id="1">
				<text class="">预约挂号</text>
			</view>
			<view class="cu-item service-nav_1" :class="2==Tab?'bg-orange cur':'bg-cyan'" @tap="goMore('/pages/index/index_healthy/index_services')" data-id="2">
				<text class="">卫生服务中心</text>
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar">
			<view class="cu-item" @tap="goMore('/pages/index/index_healthy/index_service_detail')">
				<view class="content">
					<view class="text-black">北城社区服务中心</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red  margin-right-xs"></text>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item " @tap="goMore('/pages/index/index_healthy/index_service_detail')">
				<view class="content">
					<view class="text-black">南城社区服务中心</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red  margin-right-xs"></text>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item cur" @tap="goMore('/pages/index/index_healthy/index_service_detail')">
				<view class="content">
					<view class="text-black">西城社区服务中心</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red  margin-right-xs"></text>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item cur" @tap="goMore('/pages/index/index_healthy/index_service_detail')">
				<view class="content">
					<view class="text-black">东城社区服务中心</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red  margin-right-xs"></text>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item cur" @tap="goMore('/pages/index/index_healthy/index_service_detail')">
				<view class="content">
					<view class="text-black">葡萄园社区服务中心</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red  margin-right-xs"></text>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
		</view>
		<!-- <view class="cu-bar bg-white solid-bottom line-gray">
			<view class="action">
			</view>
			<view class="action">
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
			</view>
		</view> -->
		
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
				Tab: 2,
				scroll: 0,
				scrollLeft: 0,
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
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
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.cu-btn{
	color: #333333; 
	width: 150rpx; 
	background-color: #f0ad79;
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
			width: 235upx;
			height: 85upx;
			padding: 0;
			text-align: center;
			border: #DDDDDD 1upx solid;
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
.cu-list.menu-avatar>.cu-item .content {
	position: absolute;
	left: 30upx;
	width: calc(100% - 96upx - 60upx - 120upx - 20upx);
	line-height: 1.6em;
}
.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
</style>
