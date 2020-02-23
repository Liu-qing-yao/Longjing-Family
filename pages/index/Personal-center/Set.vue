<template>
	<view>
		<view class="box top">
			<!-- <view class="cu-bar bg-gray">
				<view class="action">
					<text class="cuIcon-close"></text>我的-设置
				</view>
				<view style="padding-right: 40upx;"  @tap="goMore('/pages/index/Personal-center/My-news')">
					<image src="../../../static/input/new.png" mode="" style="width: 50upx; height: 40upx;"></image>
				</view>
			</view> -->
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/Personal-center/Personal-center')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					设置
				</view>
			</view>
		</view>
		 
		<view class="list" v-for="(list,list_i) in severList" :key="list_i">
			<view class="li" v-for="(li,li_i) in list" @tap="gotoUrl(li)" v-bind:class="{'noborder':li_i==list.length-1}"  hover-class="hover" :key="li.name" >
				<view class="text">{{li.name}}</view>
				<image class="to" src="../../../static/input/形状6拷贝7@2x.png"></image>
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
				userinfo:{},
				severList:[
					[
						{
							name:'字体设置',
							url: '/pages/index/Personal-center/Font-size',
						},
						{
							name:'关于龙井人家',
							url: '/pages/index/Personal-center/About',
						}
					]
				],
			};
		},
		onLoad() {
			//加载
			this.init();
		},
		methods: {
			init() {
				//用户信息
				this.userinfo={
					face:'../../static/HM-PersonalCenter/face.jpeg',
					username:"李明明",
					integral:"14355900"
				}		
			},
			//用户点击订单类型
			toOrderType(index){
				uni.showToast({title: this.orderTypeLise[index].name});
			},
			//用户点击列表项
			toPage(list_i,li_i){
				uni.showToast({title: this.severList[list_i][li_i].name});
			},
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
		}
	}
</script>

<style lang="scss">

.header{
	&.status{padding-top:var(--status-bar-height);}
	background-color:#fffff;width:100%;height:150upx;padding:10upx 4%;display:flex;align-items:center;
	.userinfo{
		width:90%;display:flex;
	.face{flex-shrink:0;width:15vw;height:15vw;
			image{width:100%;height:100%;border-radius:100%}
		}
	.info{
			display:flex;flex-flow:wrap;padding-left:30upx;
	.username{width:100%;color:#000;font-size:40upx}
	.integral{display:flex;align-items:center;padding:0;height:40upx;color:#000;border-radius:20upx;font-size:30upx}
		}
	}
	.setting{
		flex-shrink:0;width:6vw;height:6vw;
		image{width:100%;height:100%}
	}
}
.hover{background-color:#eee}
.orders{
	background-color:#ff6364;width:100%;height:11vw;padding:0 4%;margin-bottom:calc(11vw + 40upx);display:flex;align-items:flex-start;border-radius:0 0 100% 100%;margin-top: -1upx;
.box{
		width:98%;padding:0 1%;height:22vw;background-color:#fefefe;border-radius:24upx;box-shadow:0 0 20upx rgba(0,0,0,0.15);margin-bottom:40upx;display:flex;align-items:center;justify-content:center;
.label{
			display:flex;align-items:center;justify-content:center;flex-flow:wrap;width:100%;height:16vw;color:#666666;font-size:26upx;
.icon{
				position:relative;width:7vw;height:7vw;margin:0 1vw;
.badge{position:absolute;width:4vw;height:4vw;background-color:#ec6d2c;top:-1vw;right:-1vw;border-radius:100%;font-size:20upx;color:#fff;display:flex;align-items:center;justify-content:center;z-index: 10;}
				image{width:7vw;height:7vw;z-index: 9;}
			}
		}
	}
}
.list{
	width:100%;border-bottom:solid 26upx #f1f1f1;
	background-color: #FFFFFF;
.li{
		width:100%;height:100upx;padding:0 4%;border-bottom:solid 1upx #e7e7e7;display:flex;align-items:center;
	&.noborder{border-bottom:0}
.icon{
			flex-shrink:0;width:50upx;height:50upx;
			image{width:50upx;height:50upx}
		}
.text{padding-left:20upx;width:100%;color:#666}
.to{flex-shrink:0;width:20upx;height:30upx}
	}
}
</style>
