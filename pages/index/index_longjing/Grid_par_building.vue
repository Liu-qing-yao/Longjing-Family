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
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					网格党建
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav align-center solid-bottom">
			<view class="cu-item service-nav_1" :class="0==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_longjing/Grid_par_building')" data-id="0">
				<text class="" >网格党建</text>
			</view>
			<view class="cu-item service-nav_1" :class="1==Tab?'bg-red cur':'bg-orange'" @tap="goMore('/pages/index/index_longjing/community-par-building1')" data-id="1">
				<text>小区党建</text>
			</view>
		</scroll-view>
		<view class="cu-list menu-avatar">
			<view class="service-intro">
			    <view class="text-black text-center" style="font-size: 32upx;padding: 20upx 0;">区域党委“三张清单”公示</view>
				<view class="padding-lr txtmodle " >
					<view>
						<view class="text-orange text-center" style="padding: 15upx; font-size: 32upx;">钟鼓楼区域</view>
						<view class="flex justify-between bg-white">
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="">
								<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
						</view>
					</view>
					<view>
						<view class="text-orange text-center" style="padding: 15upx; font-size: 32upx;">大观楼区域</view>
						<view class="flex justify-between bg-white">
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="">
								<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
						</view>
					</view>
					<view>
						<view class="text-orange text-center" style="padding: 15upx; font-size: 32upx;">金沙江区域</view>
						<view class="flex justify-between bg-white" style="height: 100upx;">
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="">
								<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
							<view class="" >
								<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Listdetails')" data-target="gridModal">资源清单</button>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="service-intro">
			    <view class="text-black text-center" style="font-size: 32upx;padding: 20upx 0;">党建网格划分及网格员公布</view>
				<view class="padding-lr txtmodle " >
				 	<view class="flex justify-between bg-white" style="padding: 20upx 0;">
				 		<view class="" >
				 			<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details2')" data-target="gridModal">钟鼓楼区域</button>
				 		</view>
						<view class="">
							<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">中山社区</button>
						</view>
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')"  data-target="gridModal">西街社区</button>
						</view>
				 	</view>
					<view class="flex justify-between bg-white" style="padding: 20upx 0;">
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')"  data-target="gridModal">中山社区</button>
						</view>
						<view class="">
							<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')"  data-target="gridModal">西街社区</button>
						</view>
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">北街社区</button>
						</view>
					</view>
					<view class="flex justify-between bg-white" style="padding: 20upx 0;">
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">西街社区</button>
						</view>
						<view class="">
							<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">前进社区</button>
						</view>
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">金沙江社区</button>
						</view>
					</view>
					<view class="flex justify-between bg-white" style="padding: 20upx 0; height: 120upx;">
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">金沙江社区</button>
						</view>
						<view class="">
							<button class="cu-btn bg-white text-black"  style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">北街社区</button>
						</view>
						<view class="" >
							<button class="cu-btn bg-white text-black" style="border: #797979 1upx solid;" @tap="goMore('/pages/index/index_longjing/Grid_com_details')" data-target="gridModal">西街社区</button>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bg-white text-black" style="padding: 30upx 60upx 15upx; font-size: 32upx;">问卷调查</view>
		<view class="bg-white flex justify-between" style="padding: 0 60upx 20upx;">
			<view class="" >
				<button class="bg-orange text-white" style="font-size: 22upx; padding: 0 10upx;" @tap="showModal" data-target="gridModal">
					<view>我是居民</view>
					<text>(点击进入需求问卷)</text>
				</button>
			</view>
			<view class="" >
				<button class="bg-orange text-white" style="font-size: 22upx; padding: 0 10upx;" @tap="showModal" data-target="gridModal">
					<view>我是商户</view>
					<text></text>(点击进入需求问卷)
				</button>
			</view>
		</view>
		
		<view style="height: 90upx;"></view>
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
				botton: 0,
				scrollLeft: 0,
				scroll: 0,
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
	border: #797979 2upx solid;
	margin: 0 60upx;
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
.cu-btn{
	width: 160upx;
	padding: 0;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	padding: 0 10upx;
	display: flex;
	justify-content: space-between;
}
.service-nav_1{
		/* background: #5ddad4; */
		margin: 10upx 0 10upx 8upx;
		border-radius: 15upx;
		width: 190upx;
		height: 80upx;
		line-height: 80upx;
		padding: 0;
		text-align: center;
		border: #DDDDDD 1upx solid;
	}

</style>

