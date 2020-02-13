<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		

		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>益路有你-积分兑换
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
					积分商城
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<view class="flex bg-white solid-top solid-bottom">
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/形状557.png" mode="" style="width: 30upx;height: 30upx; padding: 0; margin-right: 12upx;"></image>
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
		<scroll-view scroll-x class="bg-white nav" style="text-align: center; border-bottom: #DDDDDD 2upx solid;">
			<view class="flex text-center">
				<view class="cu-item flex-sub" :class="index==TabCur?'text-red cur':''" v-for="(item,index) in List" :key="index" @tap="tabSelect" :data-id="index">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		<view class="bg-white">
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange" @tap="showModalS1" data-target="Modal" style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS1=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								兑换成功！
							</view>
							<view class=""  @tap="hideModalS1" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange" @tap="showModalS2" data-target="Modal" style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS2=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								已兑换完！
							</view>
							<view class=""  @tap="hideModalS2" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange" @tap="showModalS3" data-target="Modal" style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS3=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								兑换成功！
							</view>
							<view class=""  @tap="hideModalS3" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange" @tap="showModalS4" data-target="Modal"  style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS4=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								已兑换完！
							</view>
							<view class=""  @tap="hideModalS4" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="flex justify-around bg-white padding-top">
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange"  @tap="showModalS5" data-target="Modal"  style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS5=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								已兑换完！
							</view>
							<view class=""  @tap="hideModalS5" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
				<view class="mall_contents bg-white flex" style="border: #929191 1upx solid;border-radius: 10upx;">
					<view>
						<image src="../../../static/input/图层11拷贝2.png" mode="" style=" padding: 5upx;width: 180upx;height: 200upx;"></image>
					</view>
					<view class="" style="line-height: 35upx; padding: 5upx;">
						<view class="text-red">商品名称</view>
						<view class="" style="font-size: 18upx;">时间：2019-12-12</view>
						<view class="" style="font-size: 18upx;">积分：0</view>
						<view class="" style="font-size: 18upx;">状态：未兑换</view>
						<button class="shadow bg-orange"  @tap="showModalS6" data-target="Modal"   style="margin: 10upx 0upx;font-size: 22upx;padding: 0;">积分兑换</button>
					</view>
					<view class="cu-modal" :class="modalNameS6=='Modal'?'show':''">
						<view class="cu-dialog solid">
							<view class="cu-bar bg-white justify-start">
								<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
							</view>
							<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
								兑换成功！
							</view>
							<view class=""  @tap="hideModalS6" style="margin: 20upx 0 15upx 550upx;">
								<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		
		<view class="cu-bar bg-white solid-bottom line-gray">
			<view class="text-black" >
				<image src="../../../static/input/城市.png" mode=""  style="width: 630rpx; height: 220upx;margin: 0; padding-bottom: 0;"></image>
				<!-- <button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal" style="position: absolute;bottom: 10upx;right: 15upx;">更多</button> -->
			</view>
		</view>
		
		<view style="height: 80upx;"></view>
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
				picker1: ['大安街道办事处', '凉高山街道办事处', '龙井街道办事处','马冲口街道办事处'],
				picker2: ['华大社区', '大楻桶社区', '广华社区','红苕地社区'],
				modalNameS1: null,
				modalNameS2: null,
				modalNameS3: null,
				modalNameS4: null,
				modalNameS5: null,
				modalNameS6: null,
				TabCur: 0,
				botton: 0,
				scrollLeft: 0,
				List: [{
					name: '最新商品'
				}, 
				{
					name: '人气商品'
				},
				{
					name: '最近消费'
				},
				{
					name: '一周热卖'
				}]
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
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
			showModalS3(e) {
				this.modalNameS3 = e.currentTarget.dataset.target
			},
			hideModalS3(e) {
				this.modalNameS3 = null
			},
			showModalS4(e) {
				this.modalNameS4 = e.currentTarget.dataset.target
			},
			hideModalS4(e) {
				this.modalNameS4 = null
			},
			showModalS5(e) {
				this.modalNameS5 = e.currentTarget.dataset.target
			},
			hideModalS5(e) {
				this.modalNameS5 = null
			},
			showModalS6(e) {
				this.modalNameS6 = e.currentTarget.dataset.target
			},
			hideModalS6(e) {
				this.modalNameS6 = null
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
