<template>
	<view>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>设置-字体设置
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Set')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					字体设置
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
				<view class="plan-unit">
					<view class="cu-chat">
						<view class="cu-item self">
							<view class="main">
								<view class="content bg-white" :style="{'font-size': dynFontSizee + 'upx'}">
									<text>预览字体大小</text>
								</view>
							</view>
							<view class="cu-avatar radius" style="background-image:url(../../../static/input/人.png);"></view>
						</view>
						<view class="cu-item">
							<view class="cu-avatar radius" style="background-image:url(../../../static/input/形状4@3x.png);"></view>
							<view class="main">
								<view class="content shadow" :style="{'font-size': dynFontSizee + 'upx'}">
									<text >拖动下方滑块设置字体大小</text>
								</view>
							</view>
						</view>
					</view>
				</view>

				<view class="padding-tb-sm uni-common-mt bg-white" style="position: absolute; bottom: 100upx;width: 100%;">			
					<view class="flex justify-between">
						<view class="uni-title padding-left">A</view>
						<view class="uni-title" style="padding-right: 100upx;">A</view>
					</view>
					<view>
					    <slider value="28"  @change="sliderChange" min="8" max="80" show-value />
					</view>	
			    </view>
		
		
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
				PageCur: '我的',
				dynFontSizee: '28'
			}
		},
		methods: {
			sliderChange(e) {
			        console.log('value 发生变化：' + e.detail.value)
					this.dynFontSizee =  e.detail.value;
			    },
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
		},
		
	}
</script>

<style lang="scss">
.huakuai{
	position: absolute;
	bottom: 100upx;
	left: 180upx;

}
.content {
	justify-content: center;
	flex-direction: column;
}

.sliderBox {
	justify-content: center;
	margin-right: 50rpx;
}

.text-center {
	justify-content: center;
}

.rowBox {
	flex-direction: row;
	align-items: center;
	justify-content: center;
}

.mrg10T {
	margin-top: 10rpx;
}

.tips {
	color: #999;
	font-size: 24rpx;
	text-align: center;
	margin-top: 100rpx;
}

.testBtn {
	margin-top: 50rpx;
}

.part {
	flex-direction: column;
	justify-content: center;
	padding-top: 20upx;
.title {
		font-size: 32rpx;
		padding: 0 30rpx;
	}
}

.part2 {
	margin-top: 20upx;
}
</style>
