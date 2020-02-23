<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_healthy/index_healthy')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					健康常识
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
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
		
		<scroll-view scroll-x class="bg-gray nav navsecond" scroll-with-animation :scroll-left="scrollLeft">
			<view class="cu-item" :class="index==TabCur?'text-red cur':''" v-for="(item,index) in List" :key="index" @tap="tabSelect" :data-id="index">
			    {{item.name}}
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar">
			<view class="cu-item" @tap="goMore('/pages/index/index_healthy/index_common_detail')"> 
				<view class="content" style="width: 720upx;">
					<view class="text-black"><image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" ></image>学校常见传染病防治知识</view>
					<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
						<view class="text-gray">2019-12-12 16:00</view>
						<view class="flex justify-left">
							<view class="text-gray">2404</view>
							<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
						</view>
					</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content"  @tap="goMore('/pages/index/index_healthy/index_common_detail')" style="width: 720upx;">
					<view class="text-black">
						<image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" ></image>
						手足口疾病
					</view>
					<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
						<view class="text-gray">2019-12-12 16:00</view>
						<view class="flex justify-left">
							<view class="text-gray">2404</view>
							<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
						</view>
					</view>
				</view>
				
			</view>
			<view class="cu-item " @tap="goMore('/pages/index/index_healthy/index_common_detail')">
				<view class="content" style="width: 720upx;">
					<view class="text-black"><image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" ></image>青少年如何防御艾滋</view>
					<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
						<view class="text-gray">2019-12-12 16:00</view>
						<view class="flex justify-left">
							<view class="text-gray">2404</view>
							<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
						</view>
					</view>
				</view>
			</view>
			<view class="cu-item cur" @tap="goMore('/pages/index/index_healthy/index_common_detail')">
				<view class="content"  style="width: 720upx;">
					<view class="text-black"><image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" ></image>学校常见传染病防治知识</view>
					<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
						<view class="text-gray">2019-12-12 16:00</view>
						<view class="flex justify-left">
							<view class="text-gray">2404</view>
							<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
						</view>
					</view>
				</view>

			</view>
			<view class="cu-item cur pic-modle">
				<view class="content" @tap="goMore('/pages/index/index_healthy/index_common_detail')">
					<view class="text-black zuo">
						<image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" style="margin-right: 30upx;"></image>
						<image src="../../../static/input/图层9.png" style="height: 200upx;width: 200upx;margin-right: 10upx;"></image>
						<view class="" style="width: 430upx;">
							<view><text class="text-title"></text>注意儿童疾病，发烧吃药趁早<br></view><br>
							<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
								<view class="text-gray">2019-12-12 16:00</view>
								<view class="flex justify-left">
									<view class="text-gray">2404</view>
									<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
								</view>
							</view>
						</view> 
					</view>
				</view>
			</view>
			<view class="cu-item cur pic-modle">
				<view class="content" @tap="goMore('/pages/index/index_healthy/index_common_detail')" style="width: 720upx;">
					<view class="zuo">
						<image src="../../../static/input/矩形10拷贝4.png" mode="" class="logo-list" style="margin-right: 30upx;"></image>
						<image src="../../../static/input/图层8.png" style="height: 200upx;width: 200upx;margin-right: 10upx;"></image>
						<view class="" style="width: 430upx;">
							<view><text class="text-title"></text>注意儿童疾病，提早疫苗接种<br></view><br>
							<view class="margin-top-sm flex justify-between align-center" style="font-size: 26upx;">
								<view class="text-gray">2019-12-12 16:00</view>
								<view class="flex justify-left">
									<view class="text-gray">2404</view>
									<view class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
								</view>
							</view>
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
				Tab: 0,
				scroll: 0,
				TabCur: 0,
				scrollLeft: 0,
				List: [{
					name: '母婴'
				}, 
				{
					name: '常见病'
				}, 
				{
					name: '慢性病'
				},
				{
					name: '两性'
				}, 
				{
					name: '养生',
				}, 
				{
					name: '健康生活'
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
.navsecond{
	border-bottom: 1upx #DDDDDD solid;
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
	width: 1000upx;
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

</style>
