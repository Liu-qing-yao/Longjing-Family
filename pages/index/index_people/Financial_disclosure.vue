<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_people/index_people')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					财务公开
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav navfirst">
			<view class="cu-item navfirst_1" :class="0==TabCur?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_people/Party_affairs')" data-id="0">
				<text class=""></text> 党务公开
			</view>
			<view class="cu-item navfirst_1" :class="1==TabCur?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_people/Village_affairs')" data-id="1">
				<text class=""></text> 居务公开
			</view>
			<view class="cu-item navfirst_1" :class="2==TabCur?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_people/Financial_disclosure')" data-id="2">
				<text class=""></text> 财务公开
			</view>
		</scroll-view>
		<view class="flex bg-white" >
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/形状559.png" mode="" style="width: 30upx;height: 30upx; padding: 0; margin-right: 8upx;"></image>
				<view>请选择分类</view>
			</view>
			<view class="mall_change img-align" style="padding-top: 15upx;">
				先选择街道
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker img-align">
						<image src="../../../static/input/under.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
			<view class="mall_change img-align" style="padding-top: 15upx;">
				再选择社区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Community" :range="picker2">
					<view class="picker img-align">
						<image src="../../../static/input/under.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
		</view>
		
		<view class="cu-list menu-avatar solid-top">
			<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" @tap="goMore('/pages/index/index_people/Three_affairs_detail')">
					<view>
						<image src="../../../static/input/图层11_1.png" mode="" style="width: 180upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 10upx;">
						<view class="text-black text-xs" style="width: 640upx;">新街社区-12月19日就业援助对象公示</view>
						<view class="text-gray text-sm flex justify-between" style="padding-top: 90upx;">
							<view class="text-cut text-xs" >
								2019-12-22  16:00
							</view> 
							<view>
								<view class="text-xs" style="width: 200upx;">2404 <image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="bg-white" style="padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="content" @tap="goMore('/pages/index/index_people/Three_affairs_detail')">
					<view class="text-gray flex" style="padding: 15upx;">
						<view class="text-center text-black text-xs">金象社区进行居民工作满意调查</view>
					</view>
					<view class="">
						<view class="flex" style="padding: 0 10upx;">
							<image src="../../../static/input/图层11_1.png" mode="" style="width: 190upx; height: 160upx; padding-right: 10upx;"></image>
							<image src="../../../static/input/图层12_1.png" mode="" style="width: 190upx; height: 160upx; "></image>
						</view>
					</view>
					<view class="margin-top-sm flex justify-between">
						<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
						<view class="action text-gray" style="padding-right: 15upx;">
							<text class="text-xs">2404</text>
							<text class="text-gray"><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
				</view>
			</view>
			<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" @tap="goMore('/pages/index/index_people/Three_affairs_detail')">
					<view>
						<image src="../../../static/input/图层11_1.png" mode="" style="width: 180upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 10upx;">
						<view class="text-black text-xs" style="width: 640upx;">葡萄园社区党员学习通知</view>
						<view class="text-gray text-sm flex justify-between" style="padding-top: 90upx;">
							<view class="text-cut text-xs" >
								2019-12-22  16:00
							</view> 
							<view>
								<view class="text-xs" style="width: 200upx;">2404 <image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
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
				TabCur: 2,
				scrollLeft: 0,
				index_Street: -1,
				index_Communities: -1,
				picker1: ['大安街道办事处', '凉高山街道办事处', '龙井街道办事处','马冲口街道办事处'],
				picker2: ['华大社区', '大楻桶社区', '广华社区','红苕地社区'],
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
		tabSelect(e) {
			this.TabCur = e.currentTarget.dataset.id;
			this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
		}
		}
	}
</script>

<style>
	
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	text-align: center;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 15upx 5upx;
		border-radius: 15upx;
		font-size: 32upx;
		width: 240upx;
		text-align: center;
		padding: 0;
		height: 85upx;
		line-height: 85upx;
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
	width: 40upx;
	height: 20upx;
	margin: 0 5upx;
}

.com_count{
	padding-top: 130upx;
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
.mall_drop_down{
	padding:10upx 16upx;
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
