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
			<view class="cu-bar bg-white search solid-top solid-bottom">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					商家活动
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="cu-list menu-avatar">
			<view class="bg-white">
				<view class="flex bg-white"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_13.png" mode="" style="width: 150upx; height: 150upx;"></image>
						</view>
						<view class="" style="line-height: 40upx; padding-left: 15upx; width: 580upx;">
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
							<view class="flex justify-between"  style="font-size: 22upx;">
								<view class="text-cut text-red" @tap="goMore('/pages/index/index_shopping/business-detail')"  >
									[查看]
								</view> 
								<button class=""  @tap="showModalS" data-target="Modal" style="background-color: #fe9148;height: 35upx; width: 140upx; font-size: 22upx; color: #FFFFFF;padding: 0;line-height: 35upx;margin: 0 0 0 100upx;">领取优惠卷</button>
								<view class="cu-modal" :class="modalNameS=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-top text-center" style="padding: 30upx; font-size: 31upx;" >
											领取成功！
										</view>
										<view class=""  @tap="hideModalS" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white" style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
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
							<view class="" @tap="goMore('/pages/index/index_shopping/business-detail')" style="font-size: 22upx;">
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
							<view class="" @tap="goMore('/pages/index/index_shopping/business-detail')" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
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
							<view class=""  @tap="goMore('/pages/index/index_shopping/business-detail')" style="font-size: 22upx;">
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
							<view class="" @tap="goMore('/pages/index/index_shopping/business-detail')" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
							</view>
						</view>
					</view>
				</view>
				<view class="flex bg-white"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
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
							<view class="" @tap="goMore('/pages/index/index_shopping/business-detail')" style="font-size: 22upx;">
								<view class="text-cut text-red">
									[查看]
								</view> 
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
				PageCur: 'Home',
				TabCur: 0,
				scrollLeft: 0,
				modalNameS: null,
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
			showModalS(e) {
				this.modalNameS = e.currentTarget.dataset.target
			},
			hideModalS(e) {
				this.modalNameS = null
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
