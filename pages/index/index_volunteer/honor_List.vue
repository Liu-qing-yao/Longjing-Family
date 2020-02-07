<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action" >
					<text class="cuIcon-close"></text> 益路有你-光荣榜
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_volunteer')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					志愿者光荣榜
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="flex bg-white solid-bottom solid-top" >
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/椭圆766拷贝.png" mode="" style="width: 26upx;height: 35upx; padding: 0; margin-right: 12upx;"></image>
				<view>请选择分类</view>
			</view>
			<view class="mall_change img-align" >
				先选择街道
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker img-align">
						<image src="../../../static/input/下.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
			<view class="mall_change img-align" >
				再选择社区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Community" :range="picker2">
					<view class="picker img-align">
						<image src="../../../static/input/下.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
		</view>
		<view class="bg-white">
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;padding: 10upx;">
					<view>
						<image src="../../../static/input/益路有你_65.png" mode="" style=" padding: 5upx;width: 260upx;height: 260upx;"></image>
					</view>
					<view class="" style="line-height: 40upx; padding: 5upx;">
						<view class="text-red">
							郭小米
							<image src="../../../static/input/椭圆6.png" mode=""  style="width: 42upx;height: 40upx; float: right;"></image>
						</view>
						<view class="" style="font-size: 22upx;">性别：女</view>
						<view class="" style="font-size: 22upx;">年龄：23</view>
						<view class="" style="font-size: 22upx;">参加志愿活动：整治黄河公园卫生</view>
						<view class="" style="font-size: 22upx;">
							爱心指数：
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						</view>
						<view class="" style="font-size: 22upx;">所属街道与社区：五粮液大道教师社区</view>
					</view>
				</view>
			</view>
			<view class="text-center padding-top">授予积分：17</view>
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;padding: 10upx;">
					<view>
						<image src="../../../static/input/益路有你_102.png" mode="" style=" padding: 5upx;width: 260upx;height: 260upx;"></image>
					</view>
					<view class="" style="line-height: 40upx; padding: 5upx;">
						<view class="text-red">
							李大宝
							<image src="../../../static/input/椭圆6.png" mode=""  style="width: 42upx;height: 40upx; float: right;"></image>
						</view>
						<view class="" style="font-size: 22upx;">性别：男</view>
						<view class="" style="font-size: 22upx;">年龄：26</view>
						<view class="" style="font-size: 22upx;">参加志愿活动：整治黄河公园卫生</view>
						<view class="" style="font-size: 22upx;">
							爱心指数：
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						</view>
						<view class="" style="font-size: 22upx;">所属街道与社区：五粮液大道教师社区</view>
					</view>
				</view>
			</view>
			<view class="text-center padding-top">授予积分：17</view>
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;padding: 10upx;">
					<view>
						<image src="../../../static/input/益路有你_124.png" mode="" style=" padding: 5upx;width: 260upx;height: 260upx;"></image>
					</view>
					<view class="" style="line-height: 40upx; padding: 5upx;">
						<view class="text-red">
							张小凡
							<image src="../../../static/input/椭圆6.png" mode=""  style="width: 42upx;height: 40upx; float: right;"></image>
						</view>
						<view class="" style="font-size: 22upx;">性别：女</view>
						<view class="" style="font-size: 22upx;">年龄：23</view>
						<view class="" style="font-size: 22upx;">参加志愿活动：整治黄河公园卫生</view>
						<view class="" style="font-size: 22upx;">
							爱心指数：
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						    <image src="../../../static/input/形状19拷贝4.png" mode="" style="width: 30upx;height: 22upx;padding-right: 5upx;"></image>
						</view>
						<view class="" style="font-size: 22upx;">所属街道与社区：五粮液大道教师社区</view>
					</view>
				</view>
			</view>
			<view class="text-center padding-tb-sm">授予积分：17</view>
		</view>
		
		
		<!-- <view class="cu-bar bg-white solid-bottom line-gray" style="border-top: #DDDDDD 1upx solid;">
			<view class="text-black flex"  >
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal" style="position: absolute;bottom: 10upx;right: 15upx;">更多</button>
			</view>
		</view> -->
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
				index_Street: -1,
				index_Communities: -1,
				picker1: ['中山街', '西街', '北街','翠屏街'],
				picker2: ['五粮液社区', '翠屏社区', '黄河公园社区'],
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
.cu-btn{
	color: #333333; 
	width: 150rpx; 
	background-color: #f0ad79;
}
.mall_drop_down{
	padding:10upx 16upx;
}
.mall_change{
	border-left: #DDDDDD 1upx solid;
	border-right: #DDDDDD 1upx solid;
	padding: 10upx 27upx;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 28upx;
}
</style>
