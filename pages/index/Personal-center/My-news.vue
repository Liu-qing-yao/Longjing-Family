<template>
	<view>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的消息
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
					我的消息
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="bg-white solid-bottom " >
				<view v-for="(item, index) in listData1" :key="index" class="flex justify-between" :data-url="listData1[index]" style="padding: 15upx 10upx;">
					<view class="flex justify-left">
						<view class="face" ><image :id="'image' + index" mode="aspectFill" :src="item.images0" style="width: 120upx; height: 100upx;"/></view>
						<view class="padding-left">
							<view class="" style="font-size: 27upx;">
							   {{ item.title }}<image :id="'image' + index" mode="aspectFill" :src="item.images1" @tap.stop="DelImg1" :data-index="index"  style="width: 27upx; height: 32upx;"/>
							</view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description1 }}
							    <image :id="'image' + index" mode="aspectFill" :src="item.images2" style="width: 34upx; height: 25upx; margin: 5upx 5upx 0;"/>
						    </view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description2 }}
							</view>
						</view>
					</view>
					<view ><image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"/></view>
				</view>
			</view>
			<view class="bg-white solid-bottom " >
				<view v-for="(item, index) in listData2" :key="index" class="flex justify-between" :data-url="listData2[index]" style="padding: 15upx 10upx;">
					<view class="flex justify-left">
						<view class="face" ><image :id="'image' + index" mode="aspectFill" :src="item.images0" style="width: 120upx; height: 100upx;"/></view>
						<view class="padding-left">
							<view class="" style="font-size: 27upx;">
							   {{ item.title }}<image :id="'image' + index" mode="aspectFill" :src="item.images1" @tap.stop="DelImg2" :data-index="index" style="width: 27upx; height: 32upx;"/>
							</view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description1 }}
							    <image :id="'image' + index" mode="aspectFill" :src="item.images2" style="width: 34upx; height: 25upx; margin: 5upx 5upx 0;"/>
						    </view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description2 }}
							</view>
						</view>
					</view>
					<view ><image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"/></view>
				</view>
			</view>
			
			<view class="bg-white solid-bottom " >
				<view v-for="(item, index) in listData3" :key="index" class="flex justify-between" :data-url="listData3[index]" style="padding: 15upx 10upx;">
					<view class="flex justify-left">
						<view class="face" ><image :id="'image' + index" mode="aspectFill" :src="item.images0" :data-index="index" style="width: 120upx; height: 100upx;"/></view>
						<view class="padding-left">
							<view class="" style="font-size: 27upx;">
							   {{ item.title }}<image :id="'image' + index" mode="aspectFill" :src="item.images1" @tap.stop="DelImg3" :data-index="index" style="width: 27upx; height: 32upx;"/>
							</view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description1 }}
						    </view>
							<view class="" style="font-size: 24upx;">
							   {{ item.description2 }}
							</view>
						</view>
					</view>
					<view ><image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 120upx;height: 80upx; margin: 10upx 10upx;"/></view>
				</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">阳光社区a栋居民养狗噪音扰民</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="img-align">
						<image src="../../../static/input/形状599拷贝@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx;"></image>
						<text class="text-orange">您的报事未受理</text>
					</view>
			</view>
			<view class="bg-white solid-top solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">芜湖社区c栋楼灯损坏</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="img-align" style="margin-right: 68upx;">
						<image src="../../../static/input/形状616@3x.png" mode="" style="width: 32upx;height: 28upx; margin: 0 8upx;"></image>
						<text class="text-blue">正在办理</text>
					</view>
			</view>
			<view class="bg-white solid-bottom flex justify-between" style="padding: 15upx 10upx;">
				    <view class="flex justify-left">
						<view class="face padding-lr" style=""><image src="../../../static/input/me1.png" mode="" style="width: 60upx; height: 50upx;"></image></view>
						<view class="padding-left">
							<view style="font-size: 27upx;">芜湖社区c栋楼灯损坏</view>
							<view style="margin: 10upx 0 0; font-size: 22upx;">2019-12-12 22：00</view>
					    </view>
					</view>
					<view class="img-align">
						<image src="../../../static/input/形状13拷贝2@3x.png" mode="" style="width: 26upx;height: 26upx; margin: 0 8upx;"></image>
						<text class="text-red">您的报事已完结</text>
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
	import uniSection from '../../../components/uni-section/uni-section.vue'
	import uniSwipeAction from '../../../components/uni-swipe-action/uni-swipe-action.vue'
	import uniSwipeActionItem from '../../../components/uni-swipe-action-item/uni-swipe-action-item.vue'
	export default {
		data() {
			return {
				PageCur: '我的',
				listData1: [
					{
						images0: '../../../static/input/头像.png',
						title: '张三（书记）',
						images1: '../../../static/input/删除.png',
						description1: '点赞',
						images2: '../../../static/input/爱心.png',
						description2: '2019-12-12 22：00',
						images3: '../../../static/input/图层860.png',
						
					},
				],
				listData2: [
					{
						images0: '../../../static/input/头像.png',
						title: '张三（书记）',
						images1: '../../../static/input/删除.png',
						description1: '点赞',
						images2: '../../../static/input/爱心.png',
						description2: '2019-12-12 22：00',
						images3: '../../../static/input/图层860.png',
						
					},
				],
				listData3: [
					{
						images0: '../../../static/input/头像.png',
						title: '张三（书记）',
						images1: '../../../static/input/删除.png',
						description1: '评论：新年快乐！',
						description2: '2019-12-12 22：00',
						images3: '../../../static/input/图层860.png',
						
					},
				]
			}
		},
		methods: {
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
			swipeChange(e) {
				console.log('返回：', e);
			},
			DelImg1(e) {
				uni.showModal({
					title: '提示信息',
					content: '确定要删除该条记录吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.listData1.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
			DelImg2(e) {
				uni.showModal({
					title: '提示信息',
					content: '确定要删除该条记录吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.listData2.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
			DelImg3(e) {
				uni.showModal({
					title: '提示信息',
					content: '确定要删除该条记录吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.listData3.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
		}
	}
</script>

<style>
.cu-list.menu-avatar>.cu-item .content {
	position: absolute;
	left: 200upx;
	line-height: 1.6em;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 24upx;
}
</style>
