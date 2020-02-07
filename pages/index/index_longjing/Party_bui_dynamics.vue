<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 龙井人家-龙井之窗
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					党建动态
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
		<view class="flex bg-white" style="border: #DDDDDD 1upx solid;">
			<view class="bg-grey mall_change" >
				<image src="../../../static/input/形状559.png" mode="" style="width: 28upx;height: 35upx;"></image>
				请选择分类
			</view>
			<view class="mall_change" >
				先选择街道
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker">
						<image src="../../../static/input/下.png" mode="" style="width: 30upx;height: 35upx;"></image>
					</view>
				</picker>
			</view>
			<view class="mall_change" >
				再选择社区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Community" :range="picker2">
					<view class="picker">
						<image src="../../../static/input/下.png" mode="" style="width: 30upx;height: 35upx;"></image>
					</view>
				</picker>
			</view>
		</view>
		
		<view class="cu-list menu-avatar bg-white">
			<view class="Service_N">
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
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
				<view class="" style="margin: 20upx;padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
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
				<view class="" style="margin: 20upx;">
					<view class="content">
						<view class="text-gray flex" style="padding: 15upx;">
							<view><image src="../../../static/input/矩形10拷贝2.png" mode="" style="width: 45upx;height: 30upx; padding-right: 5upx;"></image></view>
						    <view class="">12/18</view> 
						</view>
						<view class="" style="padding-left: 35upx;">
							<view class="" style="border-left: #f8404c 2upx solid;padding: 0 0 0 0; line-height: 60upx;">
								<view class="flex justify-between" style="padding-left: 20upx; border-bottom: #DDDDDD 1upx dashed;">
									爱在两路桥，幸福苗圃路
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
									</view>
								</view>
								<view class="flex justify-between" style="padding-left: 20upx; border-bottom: #DDDDDD 1upx dashed;">
									合江门不忘初心牢记使命
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
									</view>
								</view>
								<view class="flex justify-between" style="padding-left: 20upx; border-bottom: #DDDDDD 1upx dashed;">
									践行承诺担当、建好社区党建
									<view class="action">
										<text class="text-gray">2404</text>
										<text class="text-gray"><image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></text>
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
		</view>
		<view class="cu-bar solid-bottom line-gray" style="background-color: #d9d9d9;">
			<view class="text-black margin-left" >
				党建联盟 不忘初心 牢记使命
			</view>
			<view class="action">
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
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
				TabCur: 1,
				scrollLeft: 0,
				List: [{
					name: '党组织简介',
					url: '/pages/index/index_longjing/index_Alliance',
				}, 
				{
					name: '党建动态',
					url: '/pages/index/index_longjing/Party_bui_dynamics',
				},
				{
					name: '党建阵地',
					url: '/pages/index/index_longjing/Par_bui_position1',
				}, 
				{
					name: '党建知识',
					url: '/pages/index/index_longjing/index_Knowledge',
				}, 
				{
					name: '网格党建',
					url: '/pages/index/index_longjing/Grid_par_building',
				},
				{
					name: '在线测试',
					url: '/pages/index/index_longjing/Online_testing',
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
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
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
.service-nav{
	border-bottom: 1upx #DDDDDD solid;
	/* display: flex;
	justify-content: center; */
}
.service-nav_1{
		/* background: #5ddad4; */
		margin: 5upx 5upx;
		border-radius: 15upx;
		width: 200upx;
		/* text-align: center; */
	}
.service-nav_1 button{
	font-size: 28upx;
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
	 padding: 0;
	 
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
.mall_drop_down{
	padding:10upx 16upx;
}
.mall_change{
	border-left: #DDDDDD 1upx solid;
	border-right: #DDDDDD 1upx solid;
	padding: 10upx 29upx;
}
</style>
