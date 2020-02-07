<template>
	<view>
		 <basics v-if="PageCur=='basics'"></basics> 
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action" @tap="goMore('/pages/index/index')">
					<text class="cuIcon-close"></text>首页-龙井之窗
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search">
				<view class="action" @tap="goMore('/pages/index/index')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					龙井之窗
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../../static/input/展最新时事映最新动态你我共同成长.png" style="width: 750rpx; height: 400rpx;" mode=""></image>
		</view>
		<view class="cu-bar bg-gray solid-bottom line-gray ">
			<view class="action">
				<image src="../../../static/model/图层18.png" mode="" style="width: 50upx; height: 40upx; padding-right: 10upx;"></image>
				<view class="text-red"><text style="color: #333333; font-size: 32rpx; font-weight: 590; padding-right: 10upx;">社区公告</text></view>
				<view class="text-xs text-black">廿四季节气——今日立冬</view>
			</view>
			<view class="action">
				<button class="cu-btn bg-orange shadow" @tap="goMore('/pages/index/index_longjing/Work_dynamics')" data-target="gridModal" style="color: #333333;">更多</button>
			</view>
		</view>
		
		 <view class="cu-list grid" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList" :key="index" @tap="gotoUrl(item)" v-if="index<gridCol*2">
				<view :class="['icon-' + item.cuIcon,'text-' + item.color]" >
					 <view class="cu-tag badge" v-if="item.badge!=0" >
						<block v-if="item.badge!=1">{{item.badge>99?'99+':item.badge}}</block>
					</view> 
				</view>
				<text>{{item.name}}</text>
			</view>
		</view>
		
		<view>
			<image src="../../../static/input/图层17.png" style="width: 750rpx; height: 200rpx;"></image>
		</view>
		<view style="height: 95rpx;"></view>
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
				    cuIcon: 'ecdfdd',
					badge: 0,
					name: '时事新闻',
					url: '/pages/index/index_longjing/Current_news',
					
				}, {
					cuIcon: 'ecff', 
					badge: 0,
					name: '党建联盟',
					url: '/pages/index/index_longjing/index_Alliance',
					
				}, {
					 cuIcon: 'ecb',
					badge: 0,
					name: '工作动态',
					url: '/pages/index/index_longjing/Work_dynamics',
					
				}, {
				    cuIcon: 'eccbfa', 
					badge: 0,
					name: '社区概况',
					url: '/pages/index/index_longjing/Com_overview',
					
				}, {
					cuIcon: 'edbd', 
					badge: 0,
					name: '社区风采',
					url: '/pages/index/index_longjing/Community style',
				
				}],
				modalName: null,
				gridCol: 3,
				gridBorder: false,
				menuBorder: false,
				menuArrow: false,
				menuCard: false,
				skin: false,
				listTouchStart: 0,
				listTouchDirection: null,
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			Gridchange(e) {
				this.gridCol = e.detail.value
			},
			Gridswitch(e) {
				this.gridBorder = e.detail.value
			},
			MenuBorder(e) {
				this.menuBorder = e.detail.value
			},
			MenuArrow(e) {
				this.menuArrow = e.detail.value
			},
			MenuCard(e) {
				this.menuCard = e.detail.value
			},
			SwitchSex(e) {
				this.skin = e.detail.value
			},
				
			// ListTouch触摸开始
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},
				
			// ListTouch计算方向
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},
				
			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
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
</style>
