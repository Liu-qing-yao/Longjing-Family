<template style="background-color: #FFFFFF;">
	<view class="bg-white">
		<view class="box top bg-white">
			<view class="cu-bar bg-white search solid-bottom" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_longjing/community-par-building2')">
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
								<uni-fav :checked="checkList[3]" class="" style="margin-top: 10upx;" fg-color="#f06e72" fg-color-checked="#f06e72" bg-color-checked="none" bg-color="none" @click="favClick(3)" />
							</view>
						</view>
					</uni-popup>
				</view>
			</view>
		</view>
		
		<view class="bg-white solid-bottom ">
			<view class="" style="margin: 0 20upx ; padding-bottom: 10upx;">
				<view class="content">
					<view class="text-gray text-center" style="padding: 15upx 0;font-size: 31upx;">					
						<view class="text-center text-black">“不忘初心，牢记使命”主题教育</view>
					</view>
					<view class="margin-top-sm flex justify-around align-center">
						<view class=" text-df">2019-12-12 16:00</view>
						<view style="font-size: 27upx;">党建动态</view>
						<view class="action">
							<text class="">2404</text>
							<text class=""><image src="../../../static/input/view.png" mode="" class="count-logo"></image></text>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bg-white">
			<view class="text-black" style="background-color: #e9e9e9; margin: 20upx 30upx; padding: 10upx;border-radius: 10upx; font-size: 27upx;line-height: 37upx;">
				<text style="background-color: #ff1b31;color: #FFFFFF; margin-right: 10upx;padding: 6upx; border-radius: 5upx; font-size: 23upx; ">导读</text>            
				中共中央政治局召开专题民主生活会强调带头把不忘初心牢记使命作为终身课题始终保持共产党人的政治本色和前进动力中共中央总书记习近平主持会议并发表重要讲话
			</view>
		</view>
		<view class="bg-white text-black" style="margin: 15upx 30upx;text-indent: 40upx; font-size: 27upx; line-height: 39upx;">
			 <view class="align-center">
				 <image src="../../../static/input/图层860.png" mode="" style="height: 380upx;width: 610upx;"></image>
			 </view>
			  <text>何市镇位于自贡市东北方向，距离城区16公里，镇域面积70.6平方公里，东靠牛佛镇，西接三多寨，南临新店镇，北接内江市市中区，是大安区各乡镇的几何中心，是“内自同城发展”的桥头堡、四川省“百镇建设行动”试点镇，大安区创建全省乡村振兴先进试点镇，大安现代农业示范园区的核心乡镇。
			  </text> 
		</view>
		<view style="height: 200upx;"></view>
		<view class="bg-white text-black" style="margin: 15upx 30upx ;font-size: 26upx;">
			<view >
				上一篇：习近平对做好“三农”工作作出重要指示
			</view>
			<view >
				下一篇：习近平会见韩国总统，推动双边关系
			</view>
		</view>
		<view>
			<view class="cu-modal" :class="modalNameS=='Modal'?'show':''">
				<view class="cu-dialog solid">
					<view class="cu-bar bg-white justify-start">
						<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
					</view>
					<view class="solid-top text-center" style="padding: 30upx;" >
						分享成功！
					</view>
					<view class=""  @tap="hideModalS" style="margin: 20upx 0 15upx 550upx;">
						<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
					</view>
				</view>
			</view>
			<view class="cu-modal" :class="modalName=='Modal'?'show':''">
				<view class="cu-dialog solid ">
					<view class="cu-bar bg-white justify-start">
						<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
					</view>
					<view class="solid-top text-center" style="padding: 30upx;" >
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
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	import uniFav from '@/components/uni-fav/uni-fav.vue'
	import uniNavBar from '../../../components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		components: {
			uniSection,
			uniPopup,
			uniIcons,
			uniFav,
			uniNavBar,
		},
	    data() {
	            return {
					PageCur: 'Home',
					CustomBar: this.CustomBar,
					modalName: null,
					modalNameS: null,
					type: '',
					content: '顶部弹 popup',
					checkList: [false, false, false, false, false, false],
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
			RadioChange(e) {
				this.radio = e.detail.value
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
	    },
	}
</script>

<style>
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
	margin: 10upx 0 0 0;
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
		height: 120upx;
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
