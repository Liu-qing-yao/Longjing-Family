<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 龙井人家-龙井之窗
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_longjing')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					社区概况
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="bg-white text-red" style="border: #DDDDDD 1upx solid;padding: 15upx 0; text-align: center; font-size: 34upx;">
				社区分类
			</view>
			<view>
				<view class="text-red" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					合计门街道
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view @tap="goMore('/pages/index/index_longjing/Com_detail')">东街社区</view>
					<view>前进社区</view>
					<view>中山社区</view>
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view @tap="goMore('/pages/index/index_longjing/Com_detail')">东街社区</view>
					<view>前进社区</view>
					<view>中山社区</view>
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view @tap="goMore('/pages/index/index_longjing/Com_detail')">东街社区</view>
					<view>前进社区</view>
					<view>中山社区</view>
				</view>
			</view>
			<view>
				<view class="text-red" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					大观楼街道
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view>滨江社区</view>
					<view>涌泉社区</view>
					<view>大观楼社区</view>
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view>文星社区</view>
					<view>仁和社区</view>
					<view>中山社区</view>
				</view>
				<view class="bg-white flex justify-around" style="border-bottom: #DDDDDD 1upx solid;padding: 15upx 0;">
					<view>人民社区</view>
					<view>和平社区</view>
					<view>晋江社区</view>
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
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
	 padding: 10upx 12upx;
	 
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
.cu-list{
	position: relative;
}
.com_count{
	position: absolute;
	right: 10upx;
	bottom: 20upx;
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

</style>
