<template>
	<view class="bg-white">
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-bottom: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					乐享生活
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="" style="height: 350upx; background-image: url(../../../static/input/happy1.png);background-size: 750upx 350upx;"> 
			<view class="bg-white solid text-center align-center" style="border-radius: 60upx;width: 380upx;padding: 10upx 30upx;margin-left: 40upx; top:140upx">龙井街道办事处华大社区</view>
			<view class="bg-white solid" style="border-radius: 15upx;padding: 15upx 30upx;margin: 0 40upx; top:155upx">
				<view class="flex justify-between">
					<view>居民数<text style="color: #ffca49;">222</text>人</view>
					<view>党员数<text style="color: #ffca49;">222</text>人</view>
					<view>访问数<text style="color: #ffca49;">222</text>人</view>
				</view>
				
				<view class="flex justify-between" style="padding: 10upx 0 0 0;">
					<text>近7天动态<text style="color: #ffca49;">22</text>条</text>
					<text>近7天社区志愿活动<text style="color: #ffca49;">22</text>人</text>
				</view>
			</view>
		</view>
		<view class="bg-white" >
			<view class="flex justify-between solid" style="padding: 15upx;">
				<view class="bg-white" style="padding: 5upx 45upx">
					我要发布动态
				</view>
				<view class="margin-lr">
					<image src="../../../static/input/形状1.png" mode="" @tap="goMore('/pages/index/index_play/index_story')" style="width: 36upx; height: 36upx;"></image>
				</view>
			</view>
		   
		   <view class="text-orange" style="padding: 15upx 60upx; font-size: 33upx;">
		     	热门动态
		   </view>
		</view>
		<view class="margin-lr" v-for="(post,index) in posts" :key="index" :id="'post-'+index">
			<view class="bg-white solid" style="border-radius: 25upx; padding: 30upx 20upx; margin: 30upx 30upx 0;">
				<view class="flex justify-star">
					<view class="post-left">
						<image class="post_header" src="../../../static/input/person.png"></image>
					</view>
					<view class="padding-left">
						<view>李四</view>
						<view style="padding-top: 15upx; font-size: 24upx;">2019-12-12 22：00</view>
					</view>
				</view>
				<view>今天进行了法制教育，很有收获哦！</view>
				<view class="">
					<view class="flex justify-end padding-top-xl">
						<view class="" @tap="like(index)">
							<image :src="post.islike===0?'../../../static/input/like.png':'../../../static/input/likeed.png'" style="width: 38upx; height: 30upx; padding-right: 5upx;"></image>
							<text style="font-size: 28upx;">赞</text>
						</view>
						<view class="padding-left" @tap="comment(index)" >
							<image src="../../../static/input/talk.png" mode="" style="width: 38upx; height: 30upx; padding: 0 5upx;"></image>
							<text style="font-size: 28upx;">评论</text>
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
						<text class="comment-nickname">{{comment.username}}: <text class="comment-content">{{comment.content}}</text></text>
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
	import chatInput from '../../../components/im-chat/chatinput.vue'; //input框
	import postData from '../../../common/index/index.post.data.js';//朋友圈数据
	
	export default {
		components: {
			chatInput
		},
		data() {
			return {
				PageCur: '发现',
				
				gridCol: 3,
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
		onUnload() {
			this.max = 0,
				this.data = [],
				this.loadMoreText = "加载更多",
				this.showLoadMore = false;
		},
		onReachBottom() { //监听上拉触底事件
			console.log('onReachBottom');
			this.showLoadMore = true;
			setTimeout(() => {
				//获取数据
				if (this.posts.length < 20){//测试数据
					this.posts = this.posts.concat(this.posts);
				}else{
					this.loadMoreText = "暂无更多";
				}
			}, 1000);
		},
		onPullDownRefresh() { //监听下拉刷新动作
			console.log('onPullDownRefresh');
			// 这里获取数据
			setTimeout(function() {
				//初始化数据
				uni.stopPullDownRefresh(); //停止下拉刷新
			}, 1000);
		},
		onNavigationBarButtonTap(e) {//监听标题栏点击事件
			if (e.index == 0) {
				this.navigateTo('../publish/publish')
			}
		},
		computed:{
			
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
			test(){
				this.navigateTo('../test/test');
			},
			navigateTo(url) {
				uni.navigateTo({
					url: url
				});
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

<style scoped>
	@import url("../../../common/index/index.css");
</style>
