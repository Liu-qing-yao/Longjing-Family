<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search">
				<view class="action" @tap="goMore('/pages/index/index_people/Advice')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red ">
					建言献策
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="peo_content">
			
			<view class="bg-white padding-tb-sm solids" >
				<view>
					<view class="action1  paddinglr">
						<view class="text-black text-xl padding-left" style="padding-top: 10upx;">类型</view>
						<image src="../../../static/input/形状1051拷贝.png" class="padding-left" 
						@tap="showModal" 
						data-target="RadioModal" style="width: 65upx; height: 55upx;"></image>
					</view>
				</view>
				
				<view class="cu-modal" :class="modalName=='RadioModal'?'show':''" @tap="hideModal">
					<view class="cu-dialog" @tap.stop="">
						<radio-group class="block" @change="RadioChange">
						<view class="cu-list menu text-left">
						<view class="cu-item" v-for="(item,index) in List1" v-if="item.flag" :key="index">
						<label class="flex justify-between align-center flex-sub">
							<view class="flex-sub">{{item.name}}</view>
							<radio class="round" :class="radio=='radio' + index?'checked':''" :checked="radio=='radio' + index?true:false"
							:value="'radio' + index"></radio>
						</label>
						</view>
						</view>
						</radio-group>
					</view>
				</view>
			</view>
			<view class="solids-bottom bg-white padding-tb-sm">
				<view class=" ">
					<view class="action1 ">
						<view class="text-black text-xl padding-left">标题</view>
						<input style=" padding: 10upx 15upx 2upx; font-size: 28upx;" placeholder="请输入你的建言献策主题" name="input">
					</view>
				</view>
			</view>
			<view>
				<view class="bg-white padding">
					<view class="padding-bottom" >
						<view class="text-black padding-bottom text-xl padding-left">建议内容</view>
						<textarea class="uni-input text-xs" style="font-size: 24upx;" maxlength="-1" :disabled="modalName!=null" @input="textareaAInput" placeholder="请详细描述你的建议内容,以便我们及时改进,谢谢"></textarea>
					</view>
				</view>
				<view class="bg-white" style="height: 200upx;"></view>
				<view class="bg-white text-center padding-tb-sm">
					<view class="">
						<button class="cu-btn bg-orange" @tap="showModal" data-target="Modal">提 交</button>
						<view class="cu-modal" :class="modalName=='Modal'?'show':''">
							<view class="cu-dialog solid">
								<view class="cu-bar bg-white justify-start">
									<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
								</view>
								<view class="solid-top text-center" style="padding: 30upx;" >
									提交成功！
								</view>
								<view class=""  @tap="hideModal" style="margin: 20upx 0 15upx 550upx;">
									<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
								</view>
							</view>
						</view>
					</view>
					
				</view>
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
				modalName: null,
				radio: 'radio1',
				List1: [{
					name: '社区发展',
					flag: true,
				}, 
				{
					name: '组织建设',
					flag: true,
				}, 
				{
					name: '提升服务能力',
					flag: true,
				},
				{
					name: '信访',
					flag: true,
				},
				{
					name: '其他',
					flag: true,
				}],
				
				
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
			
			
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			RadioChange(e) {
				this.radio = e.detail.value
			},
		}
		
	}
</script>

<style>
page{
	background-color: #FFFFFF;
}
.action1{
	padding: 0 30upx;
	display: flex;
}
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
