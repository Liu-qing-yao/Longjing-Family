<template>
	<view>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的报事
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					我的报事
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		 
		 <view class="cu-list menu-avatar">
		 	<view class="flex bg-white justify-between" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
		 		<view class="flex" >
		 			<view style="padding: 15upx 20upx;">
		 				<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
		 			</view>
		 			<view class="content" style="width: 680upx;">
		 				<view class="text-gray" style="padding: 15upx;">
		 					<view class="text-black text-s">阳光社区a栋居民养狗噪音扰民</view>
		 					
		 				</view>
		 				<view class="margin-top-sm flex justify-start">
		 					<view class="text-gray text-xs" style="padding-left: 10upx; font-size: 24upx;">2019-12-23 19:00</view>
		 					<view class="img-align" style="margin-left: 200upx;">
		 						<image src="../../../static/input/形状599拷贝@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx;"></image>
		 						<text class="text-orange">未受理</text>
		 						<image src="../../../static/input/形状9@3x.png"  @tap="showModalS" data-target="Modal"  style="width: 26upx;height: 28upx; margin: 0 8upx 0 30upx;"></image>
		 						<text class="text-red"  @tap="showModalS1" data-target="Modal" >催办</text>
		 					</view>
		 				</view>
						<view class="cu-modal" :class="modalNameS1=='Modal'?'show':''">
							<view class="cu-dialog solid">
								<view class="cu-bar bg-white justify-start">
									<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
								</view>
								<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
									催办成功！
								</view>
								<view class=""  @tap="hideModalS1" style="margin: 20upx 0 15upx 550upx;">
									<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
								</view>
							</view>
						</view>
		 			</view>
		 		</view>
		 		
		 	</view>
		 	<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
		 		<view class="flex" >
		 			<view style="padding: 15upx  20upx;">
		 				<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
		 			</view>
		 			<view class="content" style="width: 680upx;">
		 				<view class="text-gray" style="padding: 15upx;">
		 					<view class="text-black text-s">阳光社区a栋居民养狗噪音扰民</view>
		 				</view>
		 				<view class="margin-top-sm flex justify-start">
		 					<view class="text-gray text-xs" style="padding-left: 10upx; font-size: 24upx;">2019-12-23 19:00</view>
		 					<view class="img-align" style="margin-left: 200upx;">
		 						<image src="../../../static/input/形状599拷贝@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx;"></image>
		 						<text class="text-orange">未受理</text>
		 						<image src="../../../static/input/形状9@3x.png" @tap="showModalS2" data-target="Modal"  style="width: 26upx;height: 28upx; margin: 0 8upx 0 30upx;"></image>
		 						<text class="text-red" @tap="showModalS2" data-target="Modal" >催办</text>
		 					</view>
		 				</view>
						<view class="cu-modal" :class="modalNameS2=='Modal'?'show':''">
							<view class="cu-dialog solid">
								<view class="cu-bar bg-white justify-start">
									<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
								</view>
								<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
									催办成功！
								</view>
								<view class=""  @tap="hideModalS2" style="margin: 20upx 0 15upx 550upx;">
									<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
								</view>
							</view>
						</view>
		 			</view>
		 		</view>
		 		
		 	</view>
			<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view style="padding: 15upx 20upx;">
						<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
					</view>
					<view class="content" style="width: 680upx;">
						<view class="text-gray" style="padding: 15upx;">
							<view class="text-black text-s">芜湖社区c栋楼灯损坏</view>
						</view>
						<view class="margin-top-sm flex justify-start">
							<view class="text-gray" style="padding-left: 10upx;font-size: 24upx;">2019-12-23 19:00</view>
							<view class="img-align" style="margin-left: 200upx;">
								<image src="../../../static/input/形状616@3x.png" mode="" style="width: 32upx;height: 28upx; margin: 0 8upx;"></image>
								<text class="text-blue">正在办理</text>
							</view>
						</view>
					</view>
				</view>
				
			</view>
			<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view style="padding: 15upx 20upx;">
						<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
					</view>
					<view class="content" style="width: 680upx;">
						<view class="text-gray" style="padding: 15upx;">
							<view class="text-black text-s">芜湖社区c栋楼灯损坏</view>
						</view>
						<view class="margin-top-sm flex justify-start">
							<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
							<view class="img-align" style="margin-left: 200upx;">
								<image src="../../../static/input/形状13拷贝2@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx 0 0;"></image>
								<text class="text-gray">已完结</text>
							</view>
						</view>
					</view>
				</view>
				
			</view>
			<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view style="padding: 15upx 20upx;">
						<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
					</view>
					<view class="content" style="width: 680upx;">
						<view class="text-gray" style="padding: 15upx;">
							<view class="text-black text-s">芜湖社区c栋楼灯损坏</view>
						</view>
						<view class="margin-top-sm flex justify-start">
							<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
							<view class="img-align" style="margin-left: 200upx;">
								<image src="../../../static/input/形状13拷贝2@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx 0 0;"></image>
								<text class="text-gray">已完结</text>
							</view>
						</view>
					</view>
				</view>
				
			</view>
			<view class="flex bg-white justify-between" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view style="padding: 15upx 20upx;">
						<image src="../../../static/input/me1.png" mode="" style="width: 50upx; height: 50upx;"></image>
					</view>
					<view class="content" style="width: 680upx;">
						<view class="text-gray" style="padding: 15upx;">
							<view class="text-black text-s">芜湖社区c栋楼灯损坏</view>
						</view>
						<view class="margin-top-sm flex justify-start">
							<view class="text-gray text-xs" style="padding-left: 10upx;">2019-12-23 19:00</view>
							<view class="img-align" style="margin-left: 200upx;">
								<image src="../../../static/input/形状13拷贝2@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx 0 0;"></image>
								<text class="text-gray">已完结</text>
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
				PageCur: '我的',
				modalNameS1: null,
				modalNameS2: null,
			};
		},
		
		methods: {
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
			showModalS1(e) {
				this.modalNameS1 = e.currentTarget.dataset.target
			},
			hideModalS1(e) {
				this.modalNameS1 = null
			},
			showModalS2(e) {
				this.modalNameS2 = e.currentTarget.dataset.target
			},
			hideModalS2(e) {
				this.modalNameS2 = null
			},
		}
	}
</script>

<style>
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 24upx;
}	
</style>
