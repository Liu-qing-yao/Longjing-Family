<template>
	<view>
		 <basics v-if="PageCur=='basics'"></basics> 
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_longjing')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					党建联盟
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="">
			<video id="video1" ref="video1" src="../../../static/input/2.mp4" 
			style="width: 750rpx; height: 450rpx;" @error="videoErrorCallback" controls></video>
		</view>
		<view class="bg-gray solid-bottom flex justify-between" style="height: 70upx;line-height: 60upx;">
			<view class="text-center">
				<text class="margin-left" style="color: #333333; font-size: 35rpx; font-weight: 590;">党建视频</text> 
			</view>
			<view class="">
				<button class="cu-btn1" @tap="goMore('/pages/index/index_longjing/Party_bui_Video')">更 多</button>
			</view>
		</view>
		
		 <view class="cu-list grid bg-white solid-bottom" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList" :key="index" @tap="gotoUrl(item)" v-if="index<gridCol*2">
				<view :class="['icon-' + item.cuIcon,'text-' + item.color]" >
					 <view class="cu-tag badge" v-if="item.badge!=0" >
						<block v-if="item.badge!=1">{{item.badge>99?'99+':item.badge}}</block>
					</view> 
				</view>
				<text>{{item.name}}</text>
			</view>
		</view>
		<view class="bg-white text-red solid-top solid-bottom" style=";padding: 15upx 0; text-align: center; font-size: 34upx;margin-top: 15upx;">
			党组织分类
		</view>
		<view class="text-red" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 25upx;">
			合计门街道党组织
		</view>
		<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
			<view @tap="goMore('/pages/index/index_longjing/Party_org_details')">东街社区</view>
			<view>前进社区</view>
			<view>中山社区</view>
		</view>
		<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
			<view @tap="goMore('/pages/index/index_longjing/Party_org_details')">东街社区</view>
			<view>前进社区</view>
			<view>中山社区</view>
		</view>
		<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
			<view @tap="goMore('/pages/index/index_longjing/Party_org_details')">东街社区</view>
			<view>前进社区</view>
			<view>中山社区</view>
		</view>
		<view class="text-red" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 25upx;">
			大观楼党组织
		</view>
		<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
			<view @tap="goMore('/pages/index/index_longjing/Party_org_details')">文星社区</view>
			<view>永权社区</view>
			<view>中山社区</view>
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
				    cuIcon: 'edbeda',
					badge: 0,
					name: '党组织简介',
					url: '/pages/index/index_longjing/index_Alliance',
				}, {
					cuIcon: 'eceaa', 
					badge: 0,
					name: '区域党建',
					url: '/pages/index/index_longjing/Grid_par_building',
				}, {
					 cuIcon: 'ec1',
					badge: 0,
					name: '党建阵地',
					url: '/pages/index/index_longjing/Par_bui_position1',
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
		onReady: function (res) {
		        this.videoContext = uni.createVideoContext('video1')
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
			 videoErrorCallback: function (e) {
			            console.log('视频错误信息:')
			            console.log(e.target.errMsg)
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
	.Illustration1{
		height: 400upx;
	}
	
</style>
