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
				<view class="text-bold text-red">
					社区风采
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="flex bg-white solid-bottom " >
			<view class="bg-gray mall_change img-align" >
				<image src="../../../static/input/形状559.png" mode="" style="width: 30upx;height: 30upx; padding: 0; margin-right: 8upx;"></image>
				<view>请选择分类</view>
			</view>
			<view class="mall_change img-align" style="padding-top: 15upx;">
				先选择街道
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Street" :range="picker1">
					<view class="picker img-align">
						<image src="../../../static/input/under.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
			<view class="mall_change img-align" style="padding-top: 15upx;">
				再选择社区
			</view>
			<view class="" style="margin: 16upx 16upx;">
				<picker @change="PickerChange" :value="index_Community" :range="picker2">
					<view class="picker img-align">
						<image src="../../../static/input/under.png" mode="" style="width: 31upx;height: 36upx;"></image>
					</view>
				</picker>
			</view>
		</view>
		
		<view class="cu-list menu-avatar">
			<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_longjing/com-style-detail')" style="padding: 10upx; border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/益路有你_11.png" mode="" style="width: 200upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black">法制宣传进社区</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="">2404 <image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
				</view>
			</view>
			<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_longjing/com-style-detail')" style="padding: 10upx;border-bottom: #DDDDDD 1upx solid;">
				<view class="flex" >
					<view>
						<image src="../../../static/input/益路有你_11.png" mode="" style="width: 200upx; height: 160upx;"></image>
					</view>
					<view class="" style="margin-left: 15upx;">
						<view class="text-black">葡萄园社区开发创文</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut" style="padding-top: 90upx;">
								<text class=" text-red  margin-right-xs"></text>
								2019-12-22  16:00
							</view> 
						</view>
					</view>
				</view>
				<view class="com_count">
					<view class="">2404 <image src="../../../static/input/view.png" mode="" class="count-logo"></image></view>
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
				index_Street: -1,
				index_Communities: -1,
				picker1: ['大安街道办事处', '凉高山街道办事处', '龙井街道办事处','马冲口街道办事处'],
				picker2: ['华大社区', '大楻桶社区', '广华社区','红苕地社区'],
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

.com_count{
	padding-top: 130upx;
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
