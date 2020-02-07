<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 龙井人家-社区商圈
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')"  >
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					品牌商家
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="text-white text-center">
				<view class="" style="height: 80upx;background-color: #ff637a;padding: 15upx;  font-size: 35upx;">店 铺 列 表</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav navfirst align-center">
			<view class="cu-item navfirst_1" :class="0==TabCur?'bg-red':'bg-gray'" @tap="tabSelect" data-id="0">
				<text class=""></text> 全 部 分 类
			</view>
			<view class="cu-item navfirst_1" :class="1==TabCur?'bg-red cur':'bg-gray'" @tap="tabSelect" data-id="1">
				<text class=""></text> 全 城
			</view>
			<view class="cu-item navfirst_1" :class="2==TabCur?'bg-red cur':'bg-gray'" @tap="tabSelect" data-id="2">
				<text class=""></text> 离 我 最 近
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar">
			<view class="bg-white">
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_08.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;">
								<text class=" text-red"></text>
								绿源超市大观楼店
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								超市
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">超</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_141.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;">
								<text class=" text-red"></text>
								江语晨小区服务
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								果蔬粮油居家生活用品
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">零</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_20.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;">
								<text class=" text-red"></text>
								正和金帝庄园服务站
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								小区生活服务
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">餐</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_38.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;">
								<text class=" text-red"></text>
								愿君连锁
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								家电用气、日用百货
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">服</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_32.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class="text-cut text-black" style="font-size: 34upx;"></text>
								智慧水果
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								新鲜水果
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">鲜</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_26.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class="text-cut text-black" style="font-size: 34upx;"></text>
								廿四季线下连锁店
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								宜宾本地应季果蔬
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">特</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_44.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;">
								<text class=" text-red"></text>
								金文鞋城总店
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								放心、实惠
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">通</view>
					</view>
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_44.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 34upx;" >
								<text class=" text-red"></text>
								塞多电脑城
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class=" text-red"></text>
								放心、实惠
							</view>
						</view>
					</view>
					<view class="flex" style="height: 40upx;">
						<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
						<view class="bg-orange margin-right" style="padding: 0 8upx;">服</view>
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
				PageCur: 'Home',
				TabCur: 0,
				scrollLeft: 0,
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
		}
	}
</script>

<style>
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	padding: 0 10upx;
	display: flex;
	justify-content: space-between;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 10upx 5upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 235upx;
		height: 80upx;
		text-align: center;
		border: #DDDDDD 1upx solid;
	}
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
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
.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
</style>
