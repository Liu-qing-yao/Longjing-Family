<template style="background-color: #FFFFFF;">
	<view class="bg-white">
		<view class="box top bg-white">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/Personal-center/My-advice')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					详情
				</view>
				<view class="action">
					<image src="../../../static/input/收藏.png" @click="togglePopup('top', 'popup')" style="width: 45rpx; height: 12rpx;"></image>
					<uni-popup class="pup-windows " ref="showpopup" :type="type" @change="change">
						<view class="popup-content">
							<view class="img-align text-right"  @tap="showModalS" data-target="Modal">
								<image src="../../../static/input/分享.png" mode="" style="width: 32upx;height: 25upx;margin: 0 5upx 0 10upx;"></image>
								<text>分享</text>
							</view>
							<view class="" @tap="showModal" data-target="Modal">
								<uni-fav :checked="checkList[3]" class="" style="margin-top: 5upx;" fg-color="#f06e72" fg-color-checked="#f06e72" bg-color-checked="none" bg-color="none" @click="favClick(3)" />
							</view>
							<view class="img-align text-right"  @tap.stop="DelImg1" :data-index="index" >
								<image src="../../../static/input/删除.png" mode="" style="width: 28upx;height: 32upx;margin: 0 5upx 0 10upx;"></image>
								<text>删除</text>
							</view>
						</view>
					</uni-popup>
				</view>
			</view>
		</view>
		<view class="bg-white">
			<view class="" style="margin: 0 20upx ; padding-bottom: 10upx;">
				<view class="content">
					<view class="text-gray text-center" style="padding: 15upx 0;font-size: 31upx;">					
						<view class="text-center text-black">近期消防火灾隐患存在，需要居民注意防患。</view>
					</view>
					<view class="margin-top-sm flex justify-around align-center">
						<view class=" text-df">2019-12-12 16:00</view>
						<view style="font-size: 27upx; color: #fb3333;">状态：未处理</view>
						<view class="action">
							<text class="">2404</text>
							<text class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bg-white solid-top" >
			<view v-for="(item, index) in listData1" :key="index" class="" :data-url="listData1[index]" style="padding: 15upx 10upx;">
				<view class="bg-white text-black"  style="margin: 15upx 30upx;text-indent: 40upx; font-size: 27upx; line-height: 39upx;"> {{ item.description1}}</view>
				<view class="bg-white">
					<view class="margin-lr" v-for="(post,index) in posts" :key="index" :id="'post-'+index">
						<view class="bg-white">
							<view class="">
								<view class="flex justify-end padding-top-xl">
									<view class="margin-lr img-align" style="font-size: 27upx;" @tap="like(index)">
										{{ item.description2}}
										<image :src="post.islike===0?'../../../static/input/like.png':'../../../static/input/likeed.png'" style="width: 38upx; height: 30upx;  margin: 0 10upx;"></image>
										{{ item.description3}}
									</view>
									<view class="margin-lr img-align" @tap="comment(index)" >
										{{ item.description5}}
										<image src="../../../static/input/talk.png" mode=""  style="width: 38upx; height: 30upx; margin: 0 10upx;"></image>
										{{ item.description4}}
									</view>
								</view>
							</view>
							<!-- 赞／评论区 -->
							<view class="bg-white"  style="margin: 0 30upx; font-size: 27upx;padding: 0;" @tap.stop="" :style="[{top:CustomBar+'px',height:'calc(20vh - ' + CustomBar + 'px)'}]">
								<view class="text-left bg-white">
									<uni-collapse accordion="true">
									    <uni-collapse-item title="3条评论回复" style="border: none;background-color: #FFFFFF;">
											<view class="" style="margin: 0 30upx;">
												<view class="footer_content">
													<image class="liked" src="../../../static/input/likeed.png"></image>
													<text class="nickname" v-for="(user,index_like) in post.like" :key="index_like">{{user.username}}</text>
												</view>
												<view class="footer_content" style="font-size: 25upx;" v-for="(comment,comment_index) in post.comments.comment" :key="comment_index" @tap="reply(index,comment_index)">
													<text class="" style="color: #7ba8e5;">
													{{ comment.username}}： </text>
													<text class="comment-content">
													{{ comment.content}}</text>
												</view>
												<view class="bg-white" style=" ">
												   <text style="color: #7ba8e5;">{{ item.description8 }}</text>
												   <text style="font-size: 25upx;">{{ item.description10}}</text>
												   <text style="color: #7ba8e5;">{{ item.description6}}</text>
												   <text style="font-size: 25upx;">{{ item.description9}}</text>
												</view>
											</view>
									    </uni-collapse-item>
									</uni-collapse>
								</view>
							</view>
							
						</view>
						<!-- 结束 post -->
					</view>
					<view class="" style="position: fixed; width: 100%; bottom: 90upx;z-index: 1024;" v-show="showInput">
						<chat-input @send-message="send_comment" @blur="blur" :focus="focus" :placeholder="input_placeholder"></chat-input>
						<!-- <chat-input @send-message="send_comment" @blur="blur" :placeholder="input_placeholder"></chat-input> -->
					</view>
					<view class="uni-loadmore" v-if="showLoadMore">{{loadMoreText}}</view> 
				</view>
			</view>
		</view>
		
		<view class="cu-modal" :class="modalNameS1=='Modal'?'show':''">
			<view class="cu-dialog solid">
				<view class="cu-bar bg-white justify-start">
					<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
				</view>
				<view class="solid-top" style="padding: 30upx;" >
					您已点赞成功！
				</view>
				<view class=""  @tap="hideModalS1" style="margin: 20upx 0 15upx 550upx;">
					<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
				</view>
			</view>
		</view>
		<view>
			<view class="cu-modal" :class="modalNameS=='Modal'?'show':''">
				<view class="cu-dialog solid">
					<view class="cu-bar bg-white justify-start">
						<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
					</view>
					<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
						分享成功！
					</view>
					<view class=""  @tap="hideModalS" style="margin: 20upx 0 15upx 550upx;">
						<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
					</view>
				</view>
			</view>
			<view class="cu-modal" :class="modalName=='Modal'?'show':''">
				<view class="cu-dialog solid">
					<view class="cu-bar bg-white justify-start">
						<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
					</view>
					<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
						收藏成功！
					</view>
					<view class=""  @tap="hideModal" style="margin: 20upx 0 15upx 550upx;">
						<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
					</view>
				</view>
			</view>
		</view>
		<view style="height: 100upx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot solid-top">
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
	import uniCollapse from '../../../components/uni-collapse/uni-collapse.vue'
	import uniCollapseItem from '../../../components/uni-collapse-item/uni-collapse-item1.vue'
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	import uniFav from '@/components/uni-fav/uni-fav.vue'
	import uniNavBar from '../../../components/uni-nav-bar/uni-nav-bar.vue'
	
	import chatInput from '../../../components/im-chat/chatinput.vue'//input框
	import postData from '../../../common/index/index.post.data1.js'//朋友圈数据
	export default {
		components: {
			uniSection,
			uniPopup,
			uniIcons,
			uniFav,
			uniNavBar,
			uniCollapse,
			uniCollapseItem,
			chatInput
		},
	    data() {
	            return {
					PageCur: '我的',
					CustomBar: this.CustomBar,
					modalName: null,
					modalNameS: null,
					modalNameS1: null,
					
					type: '',
					content: '顶部弹 popup',
					checkList: [false, false, false, false, false, false],
					listData1: [
						{
							description1: '近期消防火灾隐患严重，居民建议反馈。。。。消防知识早知道大力开展知识普及，消防演练活动。。。',
							description2: '98',
							description3: '赞',
							description4: '评论',
							description5: '4',
							description6: '张三（社区书记）评论',
							description7: '感谢你的建议',
							description8: '我',
							description9: '：谢谢书记',
							description10: '回复',
							images4: '../../../static/input/like.png',
							images5: '../../../static/input/talk.png',					
						},
					],
					gridCol: 1,
					gridBorder: false,
					menuBorder: false,
					menuArrow: false,
					menuCard: false,
					skin: false,
					listTouchStart: 0,
					listTouchDirection: null,
					posts: postData,//模拟数据
					user_id: 4,
					username: 'Liuxy',
					
					index: '',
					comment_index: '',
					
					input_placeholder: '评论', //占位内容
					focus: false, //是否自动聚焦输入框
					is_reply: false, //回复还是评论
					showInput: false, //评论输入框
					
					screenHeight: '', //屏幕高度(系统)
					platform: '',
					windowHeight: '' ,//可用窗口高度(不计入软键盘)
					
					loadMoreText: "加载中...",
					showLoadMore: false,
	            }
	        },
			mounted() {
				
				uni.getStorage({
					key: 'posts',
					success: function (res) {
						console.log(res.data);
						this.posts = res.data;
					}
				});
			
			},
			onLoad() {
				uni.getSystemInfo({ //获取设备信息
					success: (res) => {
						this.screenHeight = res.screenHeight;
						this.platform = res.platform;
					}
				});
				uni.startPullDownRefresh();
			},
			onShow() {
				uni.onWindowResize((res) => { //监听窗口尺寸变化,窗口尺寸不包括底部导航栏
					if(this.platform === 'ios'){
						this.windowHeight = res.size.windowHeight;
						this.adjust();
					}else{
						if (this.screenHeight - res.size.windowHeight > 60 && this.windowHeight <= res.size.windowHeight) {
							this.windowHeight = res.size.windowHeight;
							this.adjust();
						}
					}
				});
			},
			onHide() {
				uni.offWindowResize(); //取消监听窗口尺寸变化
			},
			onNavigationBarButtonTap(e) {//监听标题栏点击事件
				if (e.index == 0) {
					this.navigateTo('../publish/publish')
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
	    	showModalS(e) {
	    		this.modalNameS = e.currentTarget.dataset.target
	    	},
	    	hideModalS(e) {
	    		this.modalNameS = null
	    	},
			showModalS1(e) {
				this.modalNameS1 = e.currentTarget.dataset.target
			},
			hideModalS1(e) {
				this.modalNameS1 = null
			},
	    	RadioChange(e) {
	    		this.radio = e.detail.value
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
	    	ChooseCheckbox(e) {
	    		let items = this.checkbox;
	    		let values = e.currentTarget.dataset.value;
	    		for (let i = 0, lenI = items.length; i < lenI; ++i) {
	    			if (items[i].value == values) {
	    				items[i].checked = !items[i].checked;
	    				break
	    			}
	    		}
	    	},
	    	open(){
	    	         this.$refs.popup.open()
	    	      },
	    	favClick(index) {
	    		this.checkList[index] = !this.checkList[index]
	    		this.$forceUpdate()
	    	},
	    	togglePopup(type, open) {
	    		switch (type) {
	    			case 'top':
	    				this.content = '顶部弹出 popup'
	    				break
	    	
	    			case 'bottom':
	    				this.content = '底部弹出 popup'
	    				break
	    			case 'center':
	    				this.content = '居中弹出 popup'
	    				break
	    		}
	    		this.type = type
	    		this.$nextTick(() => {
	    			this.$refs['show' + open].open()
	    		})
	    	},
			
			like(index) {
				if (this.posts[index].islike === 0) {
					this.posts[index].islike = 1;
					this.posts[index].like.push({
						"uid": this.user_id,
						"username": "," + this.username
					});
				} else {
					this.posts[index].islike = 0;
					this.posts[index].like.splice(this.posts[index].like.indexOf({
						"uid": this.user_id,
						"username": "," + this.username
					}), 1);
				}
			},
			comment(index) {
				this.showInput = true; //调起input框
				this.focus = true;
				this.index = index;
			},
			adjust() { //当弹出软键盘发生评论动作时,调整页面位置pageScrollTo
				return;
				uni.createSelectorQuery().selectViewport().scrollOffset(res => {
					var scrollTop = res.scrollTop;
					let view = uni.createSelectorQuery().select("#post-" + this.index);
					view.boundingClientRect(data => {
						console.log("data:" + JSON.stringify(data));
						console.log("手机屏幕高度:" + this.screenHeight);
						console.log("竖直滚动位置" + scrollTop);
						console.log("节点离页面顶部的距离为" + data.top);
						console.log("节点高度为" + data.height);
						console.log("窗口高度为" + this.windowHeight);
			
						uni.pageScrollTo({
							scrollTop: scrollTop - (this.windowHeight - (data.height + data.top + 45)), //一顿乱算
							// scrollTop: 50, 
							duration: 300
						});
					}).exec();
				}).exec();
			},
			reply(index, comment_index) {
				this.is_reply = true; //回复中
				this.showInput = true; //调起input框
				let replyTo = this.posts[index].comments.comment[comment_index].username;
				this.input_placeholder = '回复' + replyTo;
				this.index = index; //post索引
				this.comment_index = comment_index; //评论索引
				this.focus = true;
			},
			blur: function() {
				this.init_input();
			},
			send_comment: function(message) {
			
				if (this.is_reply) {
					var reply_username = this.posts[this.index].comments.comment[this.comment_index].username;
					var comment_content = '回复' + reply_username + ':' + message.content;
				} else {
					var comment_content = message.content;
				}
				this.posts[this.index].comments.total += 1;
				this.posts[this.index].comments.comment.push({
					"uid": this.user_id,
					"username": this.username,
					"content": comment_content //直接获取input中的值
				});
				this.init_input();
			},
			init_input() {
				this.showInput = false;
				this.focus = false;
				this.input_placeholder = '评论';
				this.is_reply = false;
			},
			previewImage(imageList, image_index) {
				var current = imageList[image_index];
				uni.previewImage({
					current: current,
					urls: imageList
				});
			},
			goPublish() {
				uni.navigateTo({
					url: './publish/publish',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
	    }
	}
</script>

<style>
	@import url("../../../common/index/index.css");
page{
		background-color: #FFFFFF;
	}
.box{
	border-bottom: 1upx #DDDDDD solid;
}

.count-logo{
	width: 45upx;
	height: 20upx;
	margin: 0 5upx;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	
}
.img-align{
	margin: 0 0 0 0;
	font-size: 30upx;
}
	/* 头条小程序组件内不能引入字体 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		font-weight: normal;
		font-style: normal;
		src: url('~@/static/uni.ttf') format('truetype');
	}

	/* #endif */

	/* #ifndef APP-NVUE */
	/* .pup-windows{
		position: fixed;
		top: 80upx;
		right: 0;
	} */
	.popup-content {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		background-color: #fff;
		padding: 5upx;
		width: 120upx;
		height: 160upx;
		position: fixed;
		top: 70upx;
		right: 10upx;
		border: #CCCCCC 2upx solid;
		border-radius: 15upx;
		color: #f06e72;
		font-size: 29upx;
	}
	.example {
		padding: 0 15px 15px;
	}

	.example-info {
		padding: 15px;
		color: #3b4144;
		background: #ffffff;
	}

	.example-body {
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 25upx;
		background-color: #ffffff;
		margin: 0;
		padding: 0;
	}

	/* #endif */
	.example {
		padding: 0 15px;
	}

	.example-info {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 15px;
		color: #3b4144;
		background-color: #ffffff;
		font-size: 14px;
		line-height: 20px;
	}

	.example-info-text {
		font-size: 14px;
		line-height: 20px;
		color: #3b4144;
	}


	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}

	.word-btn-white {
		font-size: 18px;
		color: #FFFFFF;
	}

	.word-btn {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 6px;
		height: 48px;
		margin: 15px;
		background-color: #007AFF;
	}

	.word-btn--hover {
		background-color: #4ca2ff;
	}


	.example-body {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 5px 15px;
	}

	.button {
		flex: 1;
		margin: 10px 0;
	}

	

	/* 提示窗口 */
	.uni-tip {
		/* #ifndef APP-NVUE */
		display: flex;
		flex-direction: column;
		/* #endif */
		padding: 15px;
		width: 300px;
		background-color: #fff;
		border-radius: 10px;
	}

	.uni-tip-title {
		margin-bottom: 10px;
		text-align: center;
		font-weight: bold;
		font-size: 16px;
		color: #333;
	}

	.uni-tip-content {
		/* padding: 15px;
 */
		font-size: 14px;
		color: #666;
	}

	.uni-tip-group-button {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		margin-top: 20px;
	}

	.uni-tip-button {
		flex: 1;
		text-align: center;
		font-size: 14px;
		color: #3b4144;
	}

	/* 插屏广告 */
	.uni-image {
		position: relative;
	}

	.image {
		width: 200px;
		height: 200px;
	}

	.uni-image-close {
		margin-top: 20px;
		text-align: center;
	}

	/* 底部分享 */
	.uni-share {
		/* #ifndef APP-NVUE */
		display: flex;
		flex-direction: column;
		/* #endif */
		background-color: #fff;
	}

	.uni-share-title {
		line-height: 60rpx;
		font-size: 24rpx;
		padding: 15rpx 0;
		text-align: center;
	}

	.uni-share-content {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 15px;
	}

	.uni-share-content-box {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		align-items: center;
		width: 200rpx;
	}

	.uni-share-content-image {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		justify-content: center;
		align-items: center;
		width: 60rpx;
		height: 60rpx;
		overflow: hidden;
		border-radius: 10rpx;
	}

	.content-image {
		width: 60rpx;
		height: 60rpx;
	}

	.uni-share-content-text {
		font-size: 26rpx;
		color: #333;
		padding-top: 5px;
		padding-bottom: 10px;
	}

	.uni-share-btn {
		height: 90rpx;
		line-height: 90rpx;
		font-size: 14px;
		border-top-color: #f5f5f5;
		border-top-width: 1px;
		border-top-style: solid;
		text-align: center;
		color: #666;
	}
</style>
