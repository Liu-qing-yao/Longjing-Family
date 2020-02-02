<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close" ></text> 龙井人家-社区商圈
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					主题活动
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="text-white text-center">
				<view class="padding-tb" style="height: 100upx;background-color: #ff637a;  font-size: 35upx;" @tap="showModal" data-target="gridModal">全 部 分 类</view>
			</view>
		</view>
		<scroll-view scroll-x class="bg-white nav navfirst align-center">
			<view class="cu-item navfirst_1" :class="0==TabCur?'bg-red':'bg-gray'" @tap="tabSelect" data-id="0">
				<text class=""></text> 分 类 1
			</view>
			<view class="cu-item navfirst_1" :class="1==TabCur?'bg-red cur':'bg-gray'" @tap="tabSelect" data-id="1">
				<text class=""></text> 分 类 2
			</view>
			<view class="cu-item navfirst_1" :class="2==TabCur?'bg-red cur':'bg-gray'" @tap="tabSelect" data-id="2">
				<text class=""></text> 分 类 3
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar">
			<view class="bg-white">
				<view class="flex bg-white"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_13.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								刮刮卡活动开始了
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								仅限活动当天兑换奖品，预期作废，奖品数量
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[刮刮卡]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_33.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								1分钱秒杀底洞6味豆腐干
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								1分钱秒杀豆腐干
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[秒杀]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_23.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								[众创众筹]叙府槽蛋
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								宜宾特产，非遗特产，新款众筹，保价回购
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[众筹]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_13.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								廿季促销活动 刮刮卡
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								一等奖30元优惠卷5名，使用方法：满100元可
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[刮刮卡]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_53.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								金沙江社区便民服务 实惠送上门现场大转盘
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								2019年9月12日上午
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[大转盘]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_63.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx;">
							<view class="text-cut">
								<text class=" text-red"></text>
								宜宾公益行活动
							</view>
							<view class="text-cut" style="font-size: 22upx;" >
								<text class=" text-red"></text>
								爱宜宾&春苗助学网--公益行
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut">
									[募捐]
								</view>
							</view>
							<view class="" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
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
		padding: 0;
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