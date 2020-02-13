<template>
	<view>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-我的参与
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
					我的参与
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		 <scroll-view scroll-x class="bg-white nav navfirst align-center solid-bottom">
		 	<view class="cu-item par_nav_1" :class="0==TabCur?'bg-orange':'bg-lgrey'" @tap="goMore('/pages/index/Personal-center/Participation')" data-id="0">
		 		<text class=""></text>志 愿 活 动
		 	</view>
		 	<view class="cu-item par_nav_1" :class="1==TabCur?'bg-orange cur':'bg-lgrey'" @tap="goMore('/pages/index/Personal-center/Participation1')" data-id="1">
		 		<text class=""></text>生 活 动 态
		 	</view>
		 </scroll-view>
		 <view class="bg-white solid-bottom " >
		 	<view v-for="(item, index) in listData1" :key="index" class="" :data-url="listData1[index]" style="padding: 15upx 10upx;">
		 		<view class="flex justify-between">
					<view class="flex justify-left">
						<view class="face" ><image :id="'image' + index" mode="aspectFill" :src="item.images0" style="width: 100upx; height: 100upx;"/></view>
						<view class="padding-left">
							<view class="" style="font-size: 27upx;">
							   {{ item.title }}
							</view>
							<view class="" style="font-size: 24upx;margin-top: 20upx;">
							   {{ item.description1 }}
							</view>
						</view>
					</view>
					<view ><image :id="'image' + index" mode="aspectFill" :src="item.images1"  @tap.stop="DelImg1" :data-index="index"  style="width: 27upx; height: 32upx;"/></view>
				</view>
				<view> {{ item.description2}}</view>
				<view>
					<image :id="'image' + index" mode="aspectFill" :src="item.images2" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
					<image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
				</view>
				<view class="flex justify-end ">
					<view class="padding-lr"  @tap="showModalS1" data-target="Modal">
						<image :id="'image' + index" mode="aspectFill" :src="item.images4" style="width: 38upx; height: 30upx; padding-right: 5upx;"/>
						{{ item.description3}}
					</view>
					<view>
						<image :id="'image' + index" mode="aspectFill" :src="item.images5" style="width: 38upx; height: 30upx; padding-right: 5upx;"/>
						{{ item.description4}}
					</view>
				</view>
		 	</view>
		 </view>
		 <view class="cu-modal" :class="modalNameS1=='Modal'?'show':''">
		 	<view class="cu-dialog solid">
		 		<view class="cu-bar bg-white justify-start">
		 			<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
		 		</view>
		 		<view class="solid-top" style="padding: 30upx;font-size: 32upx;" >
		 			您已点赞成功！
		 		</view>
		 		<view class=""  @tap="hideModalS1" style="margin: 20upx 0 15upx 550upx;">
		 			<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
		 		</view>
		 	</view>
		 </view>
		 <view class="bg-white solid-bottom solid-top" >
		 	<view v-for="(item, index) in listData2" :key="index" class="" :data-url="listData2[index]" style="padding: 15upx 10upx;">
		 		<view class="flex justify-between">
		 					<view class="flex justify-left">
		 						<view class="face" ><image :id="'image' + index" mode="aspectFill" :src="item.images0" style="width: 100upx; height: 100upx;"/></view>
		 						<view class="padding-left">
		 							<view class="" style="font-size: 27upx;">
		 							   {{ item.title }}
		 							</view>
		 							<view class="" style="font-size: 24upx;margin-top: 20upx;">
		 							   {{ item.description1 }}
		 							</view>
		 						</view>
		 					</view>
		 					<view ><image :id="'image' + index" mode="aspectFill" :src="item.images1"  @tap.stop="DelImg2" :data-index="index"  style="width: 27upx; height: 32upx;"/></view>
		 				</view>
		 				<view> {{ item.description2}}</view>
		 				<view>
		 					<image :id="'image' + index" mode="aspectFill" :src="item.images2" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
		 					<image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
		 				</view>
		 				<view class="flex justify-end ">
		 					<view class="padding-lr" @tap="showModalS2" data-target="Modal">
		 						<image :id="'image' + index" mode="aspectFill" :src="item.images4" style="width: 38upx; height: 30upx; padding-right: 5upx;"/>
		 						{{ item.description3}}
		 					</view>
		 					<view>
		 						<image :id="'image' + index" mode="aspectFill" :src="item.images5" style="width: 38upx; height: 30upx; padding-right: 5upx;"/>
		 						{{ item.description4}}
		 					</view>
		 				</view>	
		 	</view>
			<view class="cu-modal" :class="modalNameS2=='Modal'?'show':''">
				<view class="cu-dialog solid">
					<view class="cu-bar bg-white justify-start">
						<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
					</view>
					<view class="solid-top" style="padding: 30upx;font-size: 32upx;" >
						您已点赞成功！
					</view>
					<view class=""  @tap="hideModalS2" style="margin: 20upx 0 15upx 550upx;">
						<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
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
				PageCur: '我的',
				modalNameS1: null,
				modalNameS2: null,
				TabCur: 1,
				Tab: 1,
				botton: 0,
				scrollLeft: 0,
				listData1: [
					{
						images0: '../../../static/input/人.png',
						title: '李明明',
						images1: '../../../static/input/删除.png',
						description1: '2019-12-12 22：00',
						description2: '今天进行了社区展开法制教育，很有收获哦',
						description3: '赞',
						description4: '评论',
						images2: '../../../static/input/图层860.png',
						images3: '../../../static/input/图层860.png',
						images4: '../../../static/input/爱心.png',
						images5: '../../../static/input/评论.png',					
					},
				],
				listData2: [
				{
					images0: '../../../static/input/人.png',
					title: '李明明',
					images1: '../../../static/input/删除.png',
					description1: '2019-12-12 22：00',
					description2: '今天进行了社区展开法制教育，很有收获哦',
					description3: '赞',
					description4: '评论',
					images2: '../../../static/input/图层860.png',
					images3: '../../../static/input/图层860.png',
					images4: '../../../static/input/爱心.png',
					images5: '../../../static/input/评论.png',					
				},
				],
			};
		},
		
		methods: {
		NavChange: function(e) {
			this.PageCur = e.currentTarget.dataset.cur
		},
		tabSelect(e) {
			this.TabCur = e.currentTarget.dataset.id;
			this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
		},
		Select(e) {
			this.Tab = e.currentTarget.dataset.id;
			this.scroll = (e.currentTarget.dataset.id - 1) * 60
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
		goMore(url) {
				uni.navigateTo({
					url: url
				});
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
.par_nav_1{
	width: 375upx;
	text-align: center;
	margin: 0;
	padding: 0;
	color: #ffffff;
}	
.par_nav_2{
	width: 188upx;
	text-align: center;
	margin: 5upx 0 0;
	padding: 0;
	color: #ffffff;
	float: right;
}	
.face image{
	flex-shrink:0;width:15vw;height:15vw;
	width:100%;height:100%;border-radius:100%
		}
</style>
