<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 龙井之家-民呼我应
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_people/index_people')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					网格动态
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav navfirst" scroll-with-animation :scroll-left="scrollLeft">
			<view class="cu-item navfirst_1" :class="index==TabCur?'bg-red cur':'bg-orange'" v-for="(item,index) in List" :key="index" @tap="gotoUrl(item)" :data-id="index">
			    {{item.name}}
			</view>
		</scroll-view>
		<view class="flex bg-white" >
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/形状559.png" mode="" style="width: 30upx;height: 30upx; padding: 0; margin-right: 12upx;"></image>
				<view>请选择分类</view>
			</view>
			<view class="mall_change img-align" >
				先选择街道
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker img-align">
						<image src="../../../static/input/下.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
			<view class="mall_change img-align" >
				再选择社区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Community" :range="picker2">
					<view class="picker img-align">
						<image src="../../../static/input/下.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
		</view>
		
		<view class="cu-list menu-avatar">
			<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层11_1.png" mode="" style="width: 180upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 10upx;">
						<view class="text-black text-xs" style="width: 440upx;">新街社区-12月19日就业援助对象公示</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut text-xs" style="padding-top: 90upx;">
								<text class=" text-red"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs" style="width: 200upx;">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="bg-white" style="padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="content">
					<view class="text-gray flex" style="padding: 15upx;">
						<view class="text-center text-black text-xs">富裕村纪检工作公开</view>
					</view>
					<view class="">
						<view class="flex" style="padding: 0 10upx;">
							<image src="../../../static/input/图层11_1.png" mode="" style="width: 190upx; height: 160upx; padding-right: 10upx;"></image>
							<image src="../../../static/input/图层12_1.png" mode="" style="width: 190upx; height: 160upx; "></image>
						</view>
					</view>
					<view class="margin-top-sm flex justify-between">
						<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
						<view class="action">
							<text class="text-xs">2404</text>
							<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
				</view>
			</view>
			<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层11_1.png" mode="" style="width: 180upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 10upx;">
						<view class="text-black text-xs" style="width: 440upx;">小干村党员学习通知</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut text-xs" style="padding-top: 90upx;">
								<text class=" text-red"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs" style="width: 200upx;">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
		</view>
		<view style="height: 100upx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="NavChange" data-cur="Home">
				<view class='cuIcon-cu-image'>
				<image :src="'../../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="NavChange" data-cur="消息">
				<view class='cuIcon-cu-image'>
					<!-- <image :src="'/static/tabbar/component' + [PageCur == 'component'?'_cur':''] + '.png'"></image> -->
					<image :src="'../../../static/nav/消息' + [PageCur=='消息'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='消息'?'text-red':'text-gray'">消息</view>
			</view>
			<view class="action" @click="NavChange" data-cur="发现">
				<view class='cuIcon-cu-image'>
					<!-- <image :src="'/static/tabbar/plugin' + [PageCur == 'plugin'?'_cur':''] + '.png'"></image> -->
					<image :src="'../../../static/nav/发现' + [PageCur=='发现'?'_change':''] + '.png'" style="width: 43rpx; height: 38rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='发现'?'text-red':'text-gray'">发现</view>
			</view>
			<view class="action" @click="NavChange" data-cur="我的">
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
				TabCur: 3,
				scrollLeft: 0,
				List: [{
					name: '政策发布',
					url: '/pages/index/index_people/Policy_release',
				}, 
				{
					name: '办事指南',
					url: '/pages/index/index_people/index_Guide',
				}, 
				{
					name: '三务公开',
					url: '/pages/index/index_people/Three_affairs',
				},
				{
					name: '网格动态',
					url: '/pages/index/index_people/Grid_dynamics',
				}, 
				{
					name: '你呼我应',
					url: '/pages/index/index_people/Call_me',
				}, 
				{
					name: '民生实事',
					url: '/pages/index/index_people/People_livelihood',
				},
				{
					name: '社区公告',
					url: '/pages/index/index_people/Community_announcement',
				},
				{
					name: '线下服务站',
					url: '/pages/index/index_people/Community_service',
				},
				{
					name: '建言献策',
					url: '/pages/index/index_people/Advice',
				}],
				index_Street: -1,
				index_Communities: -1,
				picker1: ['中山街', '西街', '北街','翠屏街'],
				picker2: ['五粮液社区', '翠屏社区', '黄河公园社区'],
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
		margin: 15upx 6upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 175upx;
		text-align: center;
		padding: 0;
		height: 85upx;
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
