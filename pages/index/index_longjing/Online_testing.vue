<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 党建联盟-党组织简介
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					在线测试
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="cu-list menu-avatar">
			<view class="padding-lr bg-white" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="text-center" style="padding: 15upx 0;" >
					<text class="text-black text-xl">党员在线测试题</text>
				</view>
				<view class="text-xs text-gray" style="display: flex; justify-content: space-between;">
					<view class="text-cut">
						<text class=" text-red  margin-right-xs"></text>
						2019-12-22  16:00
					</view> 
					<view class="">
						<view class="">2404 <image src="../../../static/input/椭圆8拷贝8.png" mode="" class="count-logo"></image></view>
					</view>
				</view>
			</view>
			<view class="service-intro">
				<view class="padding">
				 	<view class="txtmodle padding bg-white">
				 		<view class="text-xs" style="height: 300upx; padding-top: 10upx;">
				 			<view class="uni-form-item uni-column" style="font-size: 32upx; padding-left: 60upx;">
				 			    <view class="title">1.预备党员预备期为（）</view>
				 			        <radio-group name="radio">
				 			            <label >
				 			                <radio class="padding-tb-sm" value="radio1" /><text>一年</text>
				 			            </label><br>
				 			            <label >
				 			                <radio class="padding-tb-sm" value="radio2" /><text>半年</text>
				 			            </label><br>
										<label>
										    <radio class="padding-tb-sm" value="radio2" /><text>两年</text>
										</label><br>
				 			        </radio-group>
				 			</view>
				 		</view>
				 	</view>
					<view class="bg-white text-red padding-tb flex justify-around">
						<view class="action">
							<button class="cu-btn shadow bg-grey text-white" style="width: 180upx;" @tap="showModal" data-target="gridModal">上一题</button>
						</view>
						<view class="action">
							<button class="cu-btn shadow bg-red text-white" style="width: 180upx;" @tap="showModal" data-target="gridModal">提交答案</button>
						</view>
						<view class="action">
							<button class="cu-btn shadow bg-grey text-white" style="width: 180upx;" @tap="showModal" data-target="gridModal">下一题</button>
						</view>
					</view>
					<view class="txtmodle bg-white margin-top text-center padding" style="height: 150upx;">
						<view class="text-green">回答正确!</view>
						<view class="text-red" style="padding: 15upx 0;">回答错误,正确答案是...</view>
					</view>
				</view>
				
			</view>
		</view>
		
		<view class="bg-white text-red " style="border: #DDDDDD 1upx solid;padding: 15upx 0; font-size: 34upx;">
			<view class="action text-right padding-lr">
				<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
			</view>
		</view>
		
		<view style="height: 96rpx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="NavChange" data-cur="Home">
				<view class='cuIcon-cu-image'>
				<image :src="'../../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="NavChange" data-cur="消息">
				<view class='cuIcon-cu-image'>
					<!-- <image :src="'/static/tabbar/component' + [PageCur == 'component'?'_cur':''] + '.png'"></image> -->
					<image :src="'../../../static/nav/消息' + [PageCur=='消息'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='消息'?'text-red':'text-gray'">消息</view>
			</view>
			<view class="action" @click="NavChange" data-cur="发现">
				<view class='cuIcon-cu-image'>
					<!-- <image :src="'/static/tabbar/plugin' + [PageCur == 'plugin'?'_cur':''] + '.png'"></image> -->
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
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 15upx 5upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 220upx;
		text-align: center;
	}
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
}
.service-title{
	position: absolute;
	margin: 0;
	left: 250upx;
	color: red;
	font-size: 30upx;
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
.text-grey{
	position: absolute;
	right: 25upx;
	bottom: 10upx;
}
.zuo{
	width: 700upx;
}

.cu-list.menu-avatar>.pic-modle{
	height: 210upx;
}
.cu-list.menu-avatar>.cu-item .content>view{
	text-align: center;
} 

.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
.service-intro{
	background-color: #FFFFFF;
}

.txtmodle{
	border: #fd3838 2upx solid;
	border-radius: 15upx;
}
.party_cont{
	padding: 20upx 0 0 20upx;
	font-size: 25upx;
}
.arrow{
	width: 34upx;
	height: 34upx;
	position: absolute;
	right: 180upx;
}
.service-action{
	display: flex;
	justify-content: space-between;
}
</style>
