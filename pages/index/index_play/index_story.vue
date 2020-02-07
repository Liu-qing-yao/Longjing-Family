<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>龙井人家-玩味生活
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom">
				<view class="action">
					<image src="../../../static/input/健康驿站_06.png"  @tap="goMore('/pages/index/index_play/index_play')" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red ">
					发布动态
				</view>
				
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="bg-white">
			<view class="padding" >
				<view class="text-black padding-bottom-xs text-xl padding-left">发布内容</view>
				<textarea class="uni-input" maxlength="-1" :disabled="modalName!=null" @input="textareaAInput" placeholder="分享新鲜事"></textarea>
			</view>
			<view class="solid-bottom padding"></view>
			<view class="padding flex justify-between">
				<view class="text-black padding-bottom-xs text-xl padding-left">上传照片</view>
				<view class="action text-xl">
					{{imgList.length}}/4
				</view>
				
			</view>
			<view class="cu-form-group" style="height: 250upx;">
				<view class="grid col-4 grid-square flex-sub padding-left">
					<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage" :data-url="imgList[index]">
					 <image :src="imgList[index]" mode="aspectFill"></image>
						<view class="cu-tag bg-red" @tap.stop="DelImg" :data-index="index">
							<text class='cuIcon-close'></text>
						</view>
					</view>
					<view class="solids" @tap="ChooseImage" v-if="imgList.length<4">
						<text class='cuIcon-cameraadd'></text>
					</view>
				</view>
			</view>
			 <view>（每张照片大小不能超过1M）</view>
		</view>
		
		<view class="bg-white text-center padding-top-xl">
			<view class="">
				<button class="cu-btn bg-orange" @tap="showModal" data-target="gridModal">发 表</button>
			</view>
		</view>
		<view class="bg-white" style="height: 100upx;"></view>
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
				imgList: [],
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
			ChooseImage() {
				uni.chooseImage({
					count: 4, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: (res) => {
						if (this.imgList.length != 0) {
							this.imgList = this.imgList.concat(res.tempFilePaths)
						} else {
							this.imgList = res.tempFilePaths
						}
					}
				});
			},
			ViewImage(e) {
				uni.previewImage({
					urls: this.imgList,
					current: e.currentTarget.dataset.url
				});
			},
			DelImg(e) {
				uni.showModal({
					title: '动态',
					content: '确定要删除吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.imgList.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
		}
		
	}
</script>

<style>
.cu-btn{
	color: #FFFFFF; 
	width: 400rpx; 
	background-color: #fe9148;
}
.intro-all {
	padding: 30rpx 0;
}
.introduce{
	border:5rpx dashed #f0ad79;
	margin: 0 45rpx 0 45rpx;
	padding: 10rpx 5rpx;
	line-height: 48rpx;
	color: #fdcc6a;
}
.Illustration1{
	height: 400upx;
}
.uni-input{
	border-radius: 10upx;
	border: #DBDBDB 1upx solid;
	height: 300upx;
	width: 620upx;
	font-size: 28upx;
	padding: 10upx;
	margin: 0 auto;
	background-color: #efedec;
}
</style>
