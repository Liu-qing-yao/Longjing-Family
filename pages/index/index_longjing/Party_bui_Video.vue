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
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					党建视频
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
			
		</view>
        <view class="cu-list menu-avatar">
			<view class="flex bg-white justify-between"  @tap="goMore('/pages/index/index_longjing/video-detail')" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层1_1.png" mode="" style="width: 220upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black text-xs" style="width: 400upx;">习近平对“三农”工作做出指示</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs flex">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="flex bg-white justify-between"  @tap="goMore('/pages/index/index_longjing/video-detail')" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层1_1.png" mode="" style="width: 220upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black text-xs" style="width: 400upx;">习近平对“三农”工作做出指示</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs flex">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="flex bg-white justify-between"  @tap="goMore('/pages/index/index_longjing/video-detail')" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层2_1.png" mode="" style="width: 220upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black text-xs" style="width: 400upx;">习近平会见韩国总统，推动双边关系</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs flex">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="flex bg-white justify-between"  @tap="goMore('/pages/index/index_longjing/video-detail')" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/图层2_1.png" mode="" style="width: 220upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black text-xs" style="width: 400upx;">习近平会见韩国总统，推动双边关系</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="text-xs flex">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
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
.com_count{
	padding-top: 130upx;
	width: 200upx;
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


</style>
