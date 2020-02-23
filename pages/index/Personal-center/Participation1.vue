<template>
	<view>
		<view class="box top">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					我的参与
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
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
				<view  @tap="goMore('/pages/index/Personal-center/dynamic-detail')" >
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
				</view>
				<view>
					<image :id="'image' + index" mode="aspectFill" :src="item.images2" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
					<image :id="'image' + index" mode="aspectFill" :src="item.images3" style="width: 250upx;height: 160upx; margin: 10upx 10upx;"/>
				</view>
				<view class="bg-white solid-top" >
					<view v-for="(item, index) in listData1" :key="index" class="" :data-url="listData1[index]" style="padding: 15upx 10upx;">
						<view class="bg-white">
							<view class="" v-for="(post,index) in posts" :key="index" :id="'post-'+index">
								<view class="bg-white">
									<view class="">
										<view class="flex justify-end padding-top-xl">
											<view class="img-align" style="font-size: 27upx;" @tap="like(index)">
												<image :src="post.islike===0?'../../../static/input/like.png':'../../../static/input/likeed.png'" style="width: 38upx; height: 30upx;  margin: 0 10upx;"></image>
												{{ item.description3}}
											</view>
											<view class="margin-lr img-align" @tap="comment(index)" >
												<image src="../../../static/input/talk.png" mode=""  style="width: 38upx; height: 30upx; margin: 0 10upx;"></image>
												{{ item.description4}}
											</view>
										</view>
									</view>
									<!-- 赞／评论区 -->
									<view class="" style="background-color: #e8e8e7; border-radius: 10upx; padding: 10upx;margin: 10upx 0 0;">
										<view class="footer_content">
											<image class="liked" src="../../../static/input/likeed.png"></image>
											<text class="nickname" v-for="(user,index_like) in post.like" :key="index_like">{{user.username}}</text>
										</view>
										<view class="footer_content" v-for="(comment,comment_index) in post.comments.comment" :key="comment_index" @tap="reply(index,comment_index)">
											<text class="comment-nickname"  style="font-size: 25upx;">{{comment.username}}： <text class="comment-content">{{comment.content}}</text></text>
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
	import chatInput from '../../../components/im-chat/chatinput.vue'//input框
	import postData from '../../../common/index/index.post.data1.js'//朋友圈数据
	export default {
		components: {
			chatInput
		},
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
						images4: '../../../static/input/like.png',
						images5: '../../../static/input/talk.png',					
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
