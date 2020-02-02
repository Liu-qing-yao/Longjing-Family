<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text> 龙井人家-益路有你
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view>
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/index_volunteer/volunteer_project')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					公益活动
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="cu-list menu-avatar">
			<view class="cu-item">
				<view class="cu-avatar lg" style="background-image:url(../../../static/input/公益项目.png);"></view>
				<view class="content">
					<view class="text-orange text-sm">公益活动</view>
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
					<button class="bg-orange flex text-center" style="width: 180upx; height: 80upx; margin: 0 18upx;">
						<view class="text-center"><image src="../../../static/input/形状10.png" mode="" style="width: 35upx; height: 45upx;padding-right: 8upx;"></image></view>
						<view class="text-center" style="padding-left: 10upx;">关注</view>
					</button>
				</view>
			</view>

		</view>
		
		<scroll-view scroll-x class="bg-white nav" style="text-align: center; border-bottom: #DDDDDD 1upx solid;">
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
								<button class="bg-orange flex" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
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
								<button class="bg-orange flex" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
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
								<button class="bg-orange flex" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
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
								<button class="bg-orange flex" style="width: 180upx; height: 80upx;">
									<view class="text-center"><image src="../../../static/input/形状12拷贝3.png" mode="" style="width: 50upx; height: 30upx;padding-right: 8upx;"></image></view>
									<view class="text-center">报名</view>
								</button>
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
			
			<view class="cu-bar bg-white solid-bottom line-gray">
				<view class="action">
				</view>
				<view class="action">
					<button class="cu-btn shadow bg-orange text-black" @tap="showModal" data-target="gridModal">更多</button>
				</view>
			</view>
		</view>
		<view style="height: 100upx;"></view>
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
