<template>
	<view class="page" @touchstart="touchStart" @touchend="touchEnd">
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom">
				<view class="action">
					<image src="../../../static/input/return.png"  @tap="goMore('/pages/index/index_play/index_play')" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red ">
					发布动态
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<form>
			<view class="bg-white">
				<view class="padding uni-textarea" >
					<view class="text-black padding-bottom-xs text-xl">发布内容</view>
					<textarea class="uni-input bg-gray padding-sm" placeholder="分享新鲜事" v-model="input_content" maxlength="-1" :disabled="modalName!=null" @input="textareaAInput"  />
				</view>
				<view class="uni-list list-pd">
					<view class="uni-list-cell cell-pd">
						<view class="uni-uploader">
							<view class="padding flex justify-between">
								<view class="text-black padding-bottom-xs text-xl uni-uploader-title">上传照片</view>
								<view class="action text-xl uni-uploader-info">
									{{imgList.length}}/3
								</view>
							</view>
							<view class="uni-uploader-body">
								<view class="uni-uploader__files cu-form-group" style="height: 250upx;">
									<view class="grid col-4 grid-square flex-sub padding-left">
										<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage" :data-url="imgList[index]">
										 <image :src="imgList[index]"  mode="aspectFill"></image>
											<view class="cu-tag bg-red" @tap.stop="DelImg" :data-index="index">
												<text class='cuIcon-close'></text>
											</view>
										</view>
										<view class="solids" @tap="chooseImage" v-if="imgList.length<3">
											<text class='cuIcon-cameraadd'></text>
										</view>
									</view>
								</view>
							</view>
							<view ></view>
							<!-- 剪裁 -->
							<view class="uni-uploader-body">
								<view class="uni-uploader__files cu-form-group" style="height: 250upx;">
									<view class="grid col-4 grid-square flex-sub padding-left">
									    <view class="bg-img">
										    <image class="image" :src="path"></image>
									    </view>
									</view>
								</view>
								<kps-image-cutter @ok="onok" @cancel="oncancle" :url="url" :fixed="true" :width="200" :height="300"></kps-image-cutter>
							</view>
							<!-- 剪裁 -->
							<!-- <view class="">
							    <view class="uni-uploader-body">
							    	<view class="uni-uploader__files cu-form-group" style="height: 250upx;">
							    		<view class="grid col-4 grid-square flex-sub padding-left">
											<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage" :data-url="imgList[index]">
											 <image :src="imgList[index]" mode="aspectFill"></image>
												<view class="cu-tag bg-red" @tap.stop="DelImg" :data-index="index">
													<text class='cuIcon-close'></text>
												</view>
											</view>
							    			<view class="solids" @tap="Choose">
							    				<text class='cuIcon-cameraadd'></text>
							    			</view>
							    		</view>
							    	</view>
							    </view>
							    <image class="image" :src="path"></image>
							    <kps-image-cutter @ok="onok" @cancel="oncancle" :url="url" :fixed="true" :width="200" :height="300"></kps-image-cutter>
							</view> -->
						</view>
					</view>
					<view>（每张照片大小不能超过1M）</view>
				</view>
				
				
				<view class="footer bg-white text-center padding-top-xl">
					<button type="default" class="feedback-submit cu-btn" @click="publish" style="background-color: #fe9148;width: 350upx; color: #FFFFFF;">提交</button>
				</view>
			</view>
		</form>
		
		<view class="bg-white" style="height: 250upx;"></view>
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
	import image from '../../../common/image.js';
	import kpsImageCutter from "@/components/ksp-image-cutter/ksp-image-cutter.vue"
	
	var sourceType = [
		['camera'],
		['album'],
		['camera', 'album']
	]
	var sizeType = [
		['compressed'],
		['original'],
		['compressed', 'original']
	]
	export default {
		components: {
			kpsImageCutter
		},
		data() {
			return {
				url: "",
				path: "",
				// title: 'choose/previewImage',
				input_content:'',
				imgList: [],
				imageList: [],
				uploadFiles: [],
				shareTitle: '',
				shareImage: '',
				PageCur: 'Home',
				modalName: null,
				
				sourceTypeIndex: 2,
				sourceType: ['拍照', '相册', '拍照或相册'],
				sizeTypeIndex: 2,
				sizeType: ['压缩', '原图', '压缩或原图'],
				countIndex: 8,
				count: [1, 2, 3, 4, 5, 6, 7, 8, 9],
				
				//侧滑返回start
				startX: 0, //点击屏幕起始位置
				movedX: 0, //横向移动的距离
				endX: 0, //接触屏幕后移开时的位置
				//end
			}
		},
		onUnload() {
			this.imgList = [],
				this.sourceTypeIndex = 2,
				this.sourceType = ['拍照', '相册', '拍照或相册'],
				this.sizeTypeIndex = 2,
				this.sizeType = ['压缩', '原图', '压缩或原图'],
				this.countIndex = 8;
		},
		onLoad() {
		
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
			uploadFileShare(num) {
				let that = this;
				let uploadTask;
				num++;
				that.uploadFiles = [];
			
				if (num < 3) {
					for (var i = 0; i < that.imgList.length; i++) {
						uploadTask = uni.uploadFile({
							url: 'http://test.upload.zgllh.site/upload/',
							filePath: that.imgList[i],
							name: 'file',
							formData: {
								token: uni.getStorageSync('token')
							},
							success: res => {
								res = JSON.parse(res.data);
								if (res.code == 200) {
									that.uploadFiles.push(res.data);
									that.shareImage = res.data;
									console.log('文件上传成功！');
								} else {
									that.uploadFileShare(num);
								}
							},
							fail: res => {
								console.log('文件上传失败！');
								that.uploadFileShare(num);
							},
							complete: res => {}
						});
			
						uploadTask.onProgressUpdate(res => {
							console.log('上传进度' + res.progress);
							console.log('已经上传的数据长度' + res.totalBytesSent);
							console.log('预期需要上传的数据总长度' + res.totalBytesExpectedToSend);
						});
					}
				} else {
					console.log('上传失败，多次重试失败！');
					that.uploadFiles.push('');
				}
			},
			//ChooseImage() {
				//uni.chooseImage({
				//	count: 3, //默认9
					//sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					//sourceType: ['album'], //从相册选择
					//success: (res) => {
					//	if (this.imgList.length != 0) {
					//		this.imgList = this.imgList.concat(res.tempFilePaths)
					//	} else {
						//	this.imgList = res.tempFilePaths
						//}
				//	//}
				//});
			//},
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
			
			Choose() {
			        uni.chooseImage({
			            success: (res) => {
			                 // 设置url的值，显示控件
			                this.url = res.tempFilePaths[0];
							
			                }
			        });
			    },
			onok(ev) {
			        this.path = ev.path;
			        this.url = "";
			},
			oncancle() {
			    // url设置为空，隐藏控件
			    this.url = "";
			    },
			async publish(){
				if (!this.input_content) {
					uni.showModal({ content: '内容不能为空', showCancel: false, });
					return;
				}
				
				uni.showLoading({title:'发布中'});
				
				var location = await this.getLocation();//位置信息,可删除,主要想记录一下异步转同步处理
				var images = [];
				for(var i = 0,len = this.imgList.length; i < len; i++){
					var image_obj = {name:'image-'+i,uri:this.imgList[i]};
					images.push(image_obj);
				}
				
				uni.uploadFile({//该上传仅为示例,可根据自己业务修改或封装,注意:统一上传可能会导致服务器压力过大
					url: 'http://test.upload.zgllh.site/upload/', //仅为示例，非真实的接口地址
					files:images,//有files时,会忽略filePath和name
					filePath: '',
					name: '',
					formData: {//后台以post方式接收
						'user_id':'1',//自己系统中的用户id
						'text': this.input_content,//moment文字部分
						'longitude':location.longitude,//经度
						'latitude':location.latitude//纬度
					},
					success: (uploadFileRes) => {
						uni.hideLoading();
						uni.showToast({
							icon:'success',
							title:"发布成功"
						})
						uni.navigateBack({//可根据实际情况使用其他路由方式
							delta:1
						});
					},
					fail: (e) => {
						console.log("e: " + JSON.stringify(e));
						uni.hideLoading();
						uni.showToast({
							icon:'none',
							title:"发布失败,请检查网络"
						})
					}
				});
			},
			
			getLocation(){//h5中可能不支持,自己选择
				return new Promise((resolve, reject) => {
					uni.getLocation({
						type: 'wgs84',
						success: function (res) {
							resolve(res);
						},
						fail: (e) => {  
							reject(e);
						}
					});
				} )
			},
			
			close(e){
			    this.imgList.splice(e,1);
			},
			chooseImage: async function() {
				if (this.imgList.length === 3) {
					let isContinue = await this.isFullImg();
					console.log("是否继续?", isContinue);
					if (!isContinue) {
						return;
					}
				}
				uni.chooseImage({
					sourceType: sourceType[this.sourceTypeIndex],
					sizeType: sizeType[this.sizeTypeIndex],
					count: this.imgList.length + this.count[this.countIndex] > 3 ? 3 - this.imgList.length : this.count[this.countIndex],
					success: (res) => {
						this.url = res.tempFilePaths[0];
						this.uploadFileShare(0);
						// #ifdef APP-PLUS
						//提交压缩,因为使用了H5+ Api,所以自定义压缩目前仅支持APP平台
						var compressd = cp_images=> {
							this.imgList = this.imgList.concat(cp_images)//压缩后的图片路径
						}
						image.compress(res.tempFilePaths,compressd);
						// #endif
						
						// #ifndef APP-PLUS
						this.imgList = this.imgList.concat(res.tempFilePaths)//非APP平台不支持自定义压缩,暂时没有处理,可通过uni-app上传组件的sizeType属性压缩
						// #endif
						
					}
				})
			},
			isFullImg: function() {
				return new Promise((res) => {
					uni.showModal({
						content: "已经有3张图片了,是否清空现有图片？",
						success: (e) => {
							if (e.confirm) {
								this.imgList = [];
								res(true);
							} else {
								res(false)
							}
						},
						fail: () => {
							res(false)
						}
					})
				})
			},
			previewImage: function(e) {
				var current = e.target.dataset.src
				uni.previewImage({
					current: current,
					urls: this.imgList
				})
			},
			touchStart: function(e) {
				this.startX = e.mp.changedTouches[0].pageX;
			},
			
			touchEnd: function(e) {
				this.endX = e.mp.changedTouches[0].pageX;
				if (this.endX - this.startX > 200) {
					uni.navigateBack();
				}
			}
		}
	}
</script>

<style scoped>
	
	.footer {
		margin-top: 80upx;
	}
	
	.cell-pd {
		padding: 20upx 30upx;
	}

	.uni-textarea {
		width: auto;
		padding: 20upx 40upx;
		line-height: 1.6;
	}
	.uni-list::before {
		height: 0;
	}
	.uni-list:after {
		height: 0;
	}
	.list-pd {
		margin-top: 0;
	}
	.close-view{
	    text-align: center;
		line-height:30upx;
		height: 35upx;
		width: 35upx;
		background: #ef5350;
		color: #FFFFFF;
		position: absolute;
		top: 1upx;
		right: 1upx;
		font-size: 35upx;
		border-radius: 8upx;
	}
	.page {
		width: 750upx;
		height: 100%;
	}
	.image {
	    width: 200px;
	    height: 200px;
	}
</style>
