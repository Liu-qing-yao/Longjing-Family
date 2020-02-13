<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>益路有你-志愿服务
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_volunteer')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					志愿服务
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="cu-list menu-avatar">
			<view class="cu-item">
				<view class="cu-avatar lg" style="background-image:url(../../../static/input/志愿服务.png);"></view>
				<view class="content">
					<view class="text-orange text-sm">志愿活动</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red"></text>
							今日：0 关注：5 帖子：1
						</view> 
					</view>
					<view class="text-gray text-sm flex">
						<view class="text-cut">
							<text class=" text-red "></text>
							志愿活动公告
						</view> 
					</view>
				</view>
				<view class="">
					<button class="bg-orange flex" style="width: 180upx; height: 80upx; padding: 0 35upx; margin-right: 20upx;">
						<view class="text-center"><image src="../../../static/input/形状10.png" mode="" style="width: 35upx; height: 45upx;padding-right: 8upx;"></image></view>
						<view class="text-center">关注</view>
					</button>
				</view>
			</view>

		</view>
		
		<scroll-view scroll-x class="bg-white nav" style="text-align: center; border-bottom: #DDDDDD 2upx solid;">
			<view class="flex text-center">
				<view class="cu-item flex-sub" :class="index==TabCur?'text-red cur':''" v-for="(item,index) in List" :key="index" @tap="tabSelect" :data-id="index">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		
		<view class="cu-list menu-avatar bg-white">
			<view class=""> 
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content">
						<view class="text-gray flex" style=" font-size: 34upx;">
							<view class="text-red">宜宾市第二医院志愿者招募</view>
						</view>
						<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
							<view>
								<view class="">
								     需要人数：10人
								</view>
								<view class="">
								      开始时间：2019-12-22 16:00
								</view>
								<view class="">
								    结束时间：无
								</view>
							</view>
							<view>
								<button class="bg-orange flex" @tap="showModalS1" data-target="Modal" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
								<view class="cu-modal" :class="modalNameS1=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-top" style="padding: 30upx;font-size: 32upx;" >
											报名成功！
										</view>
										<view class=""  @tap="hideModalS1" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content">
						<view class="text-gray flex" style=" font-size: 34upx;">
							<view class="text-red">宜宾市第二医院志愿者招募</view>
						</view>
						<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
							<view>
								<view class="">
								     需要人数：10人
								</view>
								<view class="">
								      开始时间：2019-12-22 16:00
								</view>
								<view class="">
								    结束时间：无
								</view>
							</view>
							<view>
								<button class="bg-orange flex" @tap="showModalS2" data-target="Modal" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
								<view class="cu-modal" :class="modalNameS2=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
											报名成功！
										</view>
										<view class=""  @tap="hideModalS2" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content">
						<view class="text-gray flex" style=" font-size: 34upx;">
							<view class="text-red">宜宾市第二医院志愿者招募</view>
						</view>
						<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
							<view>
								<view class="">
								     需要人数：10人
								</view>
								<view class="">
								      开始时间：2019-12-22 16:00
								</view>
								<view class="">
								    结束时间：无
								</view>
							</view>
							<view>
								<button class="bg-orange flex" @tap="showModalS3" data-target="Modal" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
								<view class="cu-modal" :class="modalNameS3=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
											报名成功！
										</view>
										<view class=""  @tap="hideModalS3" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content">
						<view class="text-gray flex" style=" font-size: 34upx;">
							<view class="text-red">宜宾市第二医院志愿者招募</view>
						</view>
						<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
							<view>
								<view class="">
								     需要人数：10人
								</view>
								<view class="">
								      开始时间：2019-12-22 16:00
								</view>
								<view class="">
								    结束时间：无
								</view>
							</view>
							<view>
								<button class="bg-orange flex" @tap="showModalS4" data-target="Modal" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
								<view class="cu-modal" :class="modalNameS4=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
											报名成功！
										</view>
										<view class=""  @tap="hideModalS4" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="" style="margin: 20upx; padding-bottom: 10upx; border-bottom: #DDDDDD 1upx solid;">
					<view class="content">
						<view class="text-gray flex" style=" font-size: 34upx;">
							<view class="text-red">宜宾市第二医院志愿者招募</view>
						</view>
						<view class="flex justify-between" style="line-height: 45upx;padding-left: 5upx; font-size: 27upx;">
							<view>
								<view class="">
								     需要人数：10人
								</view>
								<view class="">
								      开始时间：2019-12-22 16:00
								</view>
								<view class="">
								    结束时间：无
								</view>
							</view>
							<view style="">
								<button class="bg-gray flex" style="padding: 0 15upx; width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状13.png" mode="" style="width: 45upx; height: 35upx;padding-right: 8upx;"></image></view>
									<view class="text-center text-white">已结束</view>
								</button>
							</view>
						</view>
					</view>
				</view>
			</view>
			<!-- <view class="cu-bar bg-white solid-bottom line-gray">
				<view class="action">
				</view>
				<view class="action">
					<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
				</view>
			</view> -->
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
				TabCur: 0,
				scrollLeft: 0,
				modalNameS1: null,
				modalNameS2: null,
				modalNameS3: null,
				modalNameS4: null,
				List: [{
					name: '全部'
				}, 
				{
					name: '最新'
				}, 
				{
					name: '热门'
				},
				{
					name: '精华'
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
.cu-list.menu-avatar>.cu-item .content {
	position: absolute;
	left: 140upx;
	width: calc(100% - 96upx - 60upx - 120upx - 20upx);
	line-height: 1.4em;
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

</style>

