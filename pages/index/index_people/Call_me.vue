<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray solid-bottom">
				<view class="action ">
					<text class="cuIcon-close"></text> 龙井人家-民呼我应
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom">
				<view class="action" @tap="goMore('/pages/index/index_people/index_people')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red ">
					你呼我应
				</view>
				
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view style="height: 1500upx; background-color: #fd7576;">
			<image src="../../../static/input/图层1312.png" mode="" style="width: 750upx; height: 280rpx;"></image>
			<view class="" style="position: absolute;top: 450upx;">
				<view style="padding: 0 35upx 5upx;">
					<view class="fir">
						<view class=" bg-white margin-bottom-sm">
							<view class="action1  paddinglr">
								<view class="text-black text-xl padding-left" style="padding-top: 10upx;">街道</view>
								<image src="../../../static/input/形状.png" class="padding-left" 
									@tap="showModal1" data-target="RadioModal1" style="width: 80upx; height: 70upx;">
								</image>
							</view>
						</view>			
						<view class="cu-modal" :class="modalName=='RadioModal1'?'show':''" @tap="hideModal1">
							<view class="cu-dialog" @tap.stop="">
								<radio-group class="block" @change="RadioChange1">
									<view class="cu-list menu text-left">
										<view class="cu-item" v-for="(item,index) in List1" :key="index">
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
					<view  class="sec">
						<view class="bg-white ">
							<view class="action1 margin-bottom-sm">
								<view class="text-black text-xl padding-left" style="padding-top: 10upx;">社区</view>
								<image src="../../../static/input/形状.png" class="padding-left" 
								    @tap="showModal2" data-target="RadioModal2" style="width: 80upx; height: 70upx;"></image>
							</view>
						</view>
						<view class="cu-modal" :class="modalName=='RadioModal2'?'show':''" @tap="hideModal2">
							<view class="cu-dialog" @tap.stop="">
								<radio-group class="block" @change="RadioChange2">
									<view class="cu-list menu text-left">
										<view class="cu-item" v-for="(item,index) in List2" :key="index">
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
						<view  class="three">
							<view class="bg-white ">
								<view class="action1 margin-bottom-sm">
									<view class="text-black text-xl padding-left" style="padding-top: 10upx;">小区</view>
									<image src="../../../static/input/形状.png" class="padding-left" 
									    @tap="showModal4" data-target="RadioModal4" style="width: 80upx; height: 70upx;"></image>
								</view>
							</view>
							<view class="cu-modal" :class="modalName=='RadioModal4'?'show':''" @tap="hideModal4">
								<view class="cu-dialog" @tap.stop="">
									<radio-group class="block" @change="RadioChange4">
										<view class="cu-list menu text-left">
											<view class="cu-item" v-for="(item,index) in List4" :key="index">
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
					<view>
						<view class="bg-white padding-bottom-xs margin-bottom-sm">
							<view class="">
								<view class="flex padding-left ">
									<view class="text-black text-xl padding-left" style="padding: 15upx 0 15upx 30upx;">类型</view>
									<image src="../../../static/input/形状.png" class="padding-left" 
										@tap="showModal3" data-target="RadioModal3" style="width: 80upx; height: 60upx;"></image>
								</view>			
								<view class="flex padding-left">
									<view class="text-black text-s padding-left">标题 </view>
									<input style="padding: 5upx 0 0 15upx; font-size: 24upx;" placeholder="请输入你的报事主题" name="input"></input>
								</view>
							</view>
						</view>
						<view class="cu-modal" :class="modalName=='RadioModal3'?'show':''" @tap="hideModal3">
							<view class="cu-dialog" @tap.stop="">
								<radio-group class="block" @change="RadioChange3">
									<view class="cu-list menu text-left">
										<view class="cu-item" v-for="(item,index) in List3" :key="index">
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
					<view>
						<view class="bg-white padding">
							<view class="padding-bottom" >
								<view class="text-black padding-bottom-xs text-xl padding-left">报事内容</view>
								<textarea class="uni-input text-xs" style="font-size: 24upx;" maxlength="-1" :disabled="modalName!=null" @input="textareaAInput" placeholder="请详细描述你的建议内容,以便我们及时改进,谢谢"></textarea>
							</view>
							<view class="padding-top flex justify-between">
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
						<view class="bg-white text-center padding-tb-sm">
							<view class="">
								<button class="cu-btn" style="background-color: #fd4f53;" @tap="goMore('/pages/index/index_people/Submit')" data-target="gridModal">发 表</button>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="" style="height: 300upx; background-color: #fd7576;"></view>
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
				PageCur: '报事',
				imgList: [],
				modalName: null,
				radio: 'radio1',
				List1: [{
					name: '大安街道',
					flag: true,
				}, 
				{
					name: '凉高山街道',
					flag: true,
				}, 
				{
					name: '龙井街道',
					flag: true,
				},
				{
					name: '马冲口街道',
					flag: true,
				}],
				
				List2: [{
					name: '华大社区',
					flag: true,
				}, 
				{
					name: '大楻桶社区',
					flag: true,
				}, 
				{
					name: '广华社区',
					flag: true,
				},
				{
					name: '红苕地社区',
					flag: true,
				}],
				List3: [{
					name: '社区发展',
					flag: false,
				}, 
				{
					name: '组织建设',
					flag: false,
				}, 
				{
					name: '提升服务能力',
					flag: false,
				},
				{
					name: '其他',
					flag: false,
				}],
				List4: [{
					name: '华大小区',
					flag: true,
				}, 
				{
					name: '大楻桶小区',
					flag: true,
				}, 
				{
					name: '广华小区',
					flag: true,
				},
				{
					name: '红苕地小区',
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
					title: '照片',
					content: '确定要删除该照片吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.imgList.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
			showModal1(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal1(e) {
				this.modalName = null
			},
			RadioChange1(e) {
				this.radio = e.detail.value
			},
			
			showModal2(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal2(e) {
				this.modalName = null
			},
			RadioChange2(e) {
				this.radio = e.detail.value
			},
			
			showModal3(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal3(e) {
				this.modalName = null
			},
			RadioChange3(e) {
				this.radio = e.detail.value
			},
			
			showModal4(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal4(e) {
				this.modalName = null
			},
			RadioChange4(e) {
				this.radio = e.detail.value
			},
		}
		
	}
</script>

<style>
.peo_content{
	background-color: #fd7576;
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
