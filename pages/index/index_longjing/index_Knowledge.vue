<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 龙井之窗-党建联盟
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					党建知识
				</view>
				<view class="action">
					<!-- <text class="cuIcon-recordfill text-red"></text> -->
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<scroll-view scroll-x class="bg-white nav navfirst" scroll-with-animation :scroll-left="scrollLeft">
			<view class="cu-item navfirst_1" :class="index==TabCur?'bg-red cur':'bg-orange'" v-for="(item,index) in List" :key="index" @tap="gotoUrl(item)" :data-id="index">
			    {{item.name}}
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar">
			<view class="flex bg-white cu-item" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
				<view class="mall_contents bg-white flex  justify-around">
					<view>
						<image src="../../../static/input/社区商圈改_20.png" mode="" style="width: 160upx; height: 120upx;"></image>
					</view>
					<view class="" style="line-height: 45upx; padding-left: 15upx;">
						<view class="text-cut text-black">
							<text class=" text-red"></text>
							一秒读懂党的第十九届四中全会公告
						</view>
						<view class="text-cut"  >
							<view class="text-gray" style="font-size: 26upx;line-height: 60upx;">
								2019-12-22  16:00
							</view >
							
						</view>
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content">
					<view class="text-black">中国共产党章程</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<view class="margin-right-xs"></view>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="cu-item ">
				<view class="content">
					<view class="text-black">中国共产党问责条例</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<view class="margin-right-xs"></view>
							2019-12-22  16:00
						</view> 
					</view>
				</view>
				<view class="action">
					<view class="text-grey text-xs">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
		</view>
		<view style="height: 400upx;"></view>
		<view class="cu-bar solid-bottom line-gray" style="background-color: #d9d9d9;">
			<view class="text-black margin-left" >
				党建联盟 不忘初心 牢记使命
			</view>
			<view class="action">
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
			</view>
		</view>
		
		<view style="height: 96rpx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="NavChange" data-cur="Home">
				<view class='cuIcon-cu-image'>
				<image :src="'../../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="NavChange" data-cur="消息">
				<view class='cuIcon-cu-image'>
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
