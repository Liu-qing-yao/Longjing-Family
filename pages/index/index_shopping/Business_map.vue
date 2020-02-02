<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 龙井之家-社区商圈
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					商圈地图
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
				
			</view>
			
		</view>
		<view class="page-body">
		    <view class="page-section page-section-gap">
		         <map style="width: 100%; height: 1100upx;" :latitude="latitude" :longitude="longitude" :markers="covers"  @markertap="showModal" data-target="Modal" ></map>
		    </view>
			<view>
				<view class="cu-modal" :class="modalName=='Modal'?'show':''">
					<view class="cu-dialog">
						<view class="cu-bar bg-white justify-end">
							<view class="content text-red">商家信息</view>
							<view class="action" @tap="hideModal">
								<text class="cuIcon-close text-red"></text>
							</view>
						</view>
						<view class="solid-bottom solid-top" style="text-align: left; padding: 10upx 25upx; line-height: 50upx;">
							<view>名称：绿源超市大观楼店</view>
							<view>联系方式：12132244</view>
							<view>联系地址：翠屏区宜宾学院48408号</view>
							<view class="text-blue">[查看详细地址]</view>
						</view>
						<view class="flex justify-around solid-bottom">
							<view class="solid-right padding-right padding-tb-sm">
								<image src="../../../static/input/椭圆703.png" mode="" style="width: 40upx; height: 30upx;"></image>
								在附近找
							</view>
							<view class="solid-right padding-right padding-tb-sm">
								<image src="../../../static/input/椭圆713.png" mode="" style="width: 20upx; height: 30upx;"></image>
								到这里去
							</view>
							<view class="padding-right padding-tb-sm">
								<image src="../../../static/input/椭圆713拷贝.png" mode="" style="width: 20upx; height: 30upx;"></image>
								从这里出发
							</view>
						</view>
						<view>
							<view class=''>
								<view class='header bg-ff row padding flex justify-between'>
									<input class="uni-input" focus placeholder='请输入地址'></input>
									<button class="cu-btn bg-gradual-red text-white" style="width: 150upx; margin-left: 10upx;">搜索</button>
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
				CustomBar: this.CustomBar,
				modalName: null,
				title: 'map',
				latitude: 39.909,
				longitude: 116.39742,
				covers: [{
					width: 30,
					height: 30,
				    latitude: 39.909,
				    longitude: 116.39742,
				    iconPath: '../../../static/input/map.png',
					id: 1,
				}
				],
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
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			RadioChange(e) {
				this.radio = e.detail.value
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
	width: 40upx;
	height: 20upx;
	margin: 0 5upx;
}
.uni-input{
	border-radius: 10upx;
	border: #b5b1b1 1upx solid;
	height: 60upx;
	width: 500upx;
	text-align: left;
	padding-left: 10upx;
}
</style>
