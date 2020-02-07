<template>
	<view>
		 <basics v-if="PageCur=='basics'"></basics> 
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gradual-red search">
				<view class="content">	
					龙井人家
				</view>
			</view>
		</view>
		<view class="Illustration1">
			<image src="../../static/model/党建引领智慧龙井开启幸福生活.png" style="width: 750rpx; height: 400rpx;" mode=""></image>
		</view>
		<view class="cu-bar bg-gray solid-bottom line-gray">
			<view class="action">
				<image src="../../static/model/图层18.png" mode="" style="width: 50upx; height: 40upx; padding-right: 10upx;"></image>
				<view class="text-red"><text style="color: #333333; font-size: 32rpx; font-weight: 590; padding-right: 10upx;">社区公告</text></view>
				<view class="text-xs text-black">廿四季节气——今日立冬</view>
			</view>
			<view class="action">
				<button class="cu-btn shadow"  @tap="goMore('/pages/index/index_people/Community_announcement')" data-target="gridModal">更多</button>
			</view>
		</view>
		<view style="text-align: center; padding-top: 12rpx;">
			<text style="font-size: 28rpx;">自贡龙井街集中开展 “春季卫生大行动” </text>
		</view>
		
		
		<view :style="{'font-size': PageCur + 'rpx'}"></view>
		
		 <view class="cu-list grid" :class="['col-' + gridCol,gridBorder?'':'no-border']">
			<view class="cu-item" v-for="(item,index) in cuIconList" :key="index" @tap="gotoUrl(item)" v-if="index<gridCol*2" >
				<view :class="['icon-' + item.cuIcon,'text-' + item.color]" >
					 <view class="cu-tag badge" v-if="item.badge!=0" >
						<block v-if="item.badge!=1">{{item.badge>99?'99+':item.badge}}</block>
					</view> 
				</view>
				<text>{{item.name}}</text>
			</view>
		</view>
		<navigator :url="'/pages/test/test?item='+ encodeURIComponent(JSON.stringify(item))"></navigator>
		<view>
			<image src="../../static/model/奉献无止境宗旨在心中.png" style="width: 750rpx; height: 150rpx;"></image>
		</view>
		<view style="height: 95rpx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="goMore('/pages/index/index')" data-cur="Home">
				<view class='cuIcon-cu-image'>
				    <image :src="'../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Call_me')" data-cur="报事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../static/nav/消息' + [PageCur=='报事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='报事'?'text-red':'text-gray'" >报事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Community_service')" data-cur="办事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../static/nav/办事' + [PageCur=='办事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='办事'?'text-red':'text-gray'" >办事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_play/index_play')" data-cur="发现">
				<view class='cuIcon-cu-image'>
					<image :src="'../../static/nav/发现' + [PageCur=='发现'?'_change':''] + '.png'" style="width: 43rpx; height: 38rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='发现'?'text-red':'text-gray'">发现</view>
			</view>
			<view class="action" @click="goMore('/pages/index/Personal-center/Personal-center')" data-cur="我的">
				<view class='cuIcon-cu-image'>
					<image :src="'../../static/nav/我的' + [PageCur=='我的'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
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
				    cuIcon: 'dfca',
					badge: 0,
					name: '龙井之窗',
					url: '/pages/index/index_longjing/index_longjing',
				}, {
					 cuIcon: 'dfcaade',
					badge: 0,
					name: '民呼我应',
					url: '/pages/index/index_people/index_people',
					
				},{
					cuIcon: 'dfdb', 
					badge: 0,
					name: '乐享生活',
					url: '/pages/index/index_play/index_play',
					
				},  {
				    cuIcon: 'dfcccb', 
					badge: 0,
					name: '益路有你',
					url: '/pages/index/index_volunteer/index_volunteer',
					
				}, {
					cuIcon: 'dfccdc', 
					badge: 0,
					name: '健康驿站',
					url: '/pages/index/index_healthy/index_healthy',
					
				}, {
					cuIcon: 'dfcade',
					badge: 0,
					name: '社区商圈',
					url: '/pages/index/index_shopping/index_shopping',
					
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
				goMore(url) {
					uni.navigateTo({
						url: url
					});
				},
			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			}
		}	
	}
</script>

<style>
.cu-btn{
	color: #333333; 
	width: 150rpx; 
	background-color: #f0ad79;
}
.intro-all {
	padding: 30rpx 0;
}
.introduce{
	border:5rpx dashed #f0ad79;
	margin: 0 45rpx 0 45rpx;
	padding: 10rpx 5rpx;
	line-height: 48rpx;
	color: #fdcc6a;
}
.Illustration1{
	height: 400upx;
}	
</style>
