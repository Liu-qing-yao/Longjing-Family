<template>
	<view class="index">
		<view class="index-ball-con">
			<view class="bgpic">
				<!-- 此处可以放背景图 -->
				<!-- <image src="../../static/cloudBall/ball.png"></image> -->
			</view>
			<view style="position:absolute;left:0;top:0;right:0;">
				<button @tap="tapCloud(index,item)" class="tree" v-bind:class="[item.hide ? 'treehide' : '']" :style="item.pos"
				 v-for="(item,index) in cloudBall" :key="index">
					<image class="ball" :src="item.imgUrl"></image>
					<text :class="item.txtCls">5000</text>
					<text :class="item.infoCls">{{item.info}}</text>
				</button>
			</view>
			<view @tap="tapMain()" class="pushFormSubmit">
				<button class="circel" formType="submit">
					<view class="today">今日步数</view>
					<view class="number">9999999</view>
					<view class="day1">点击兑换</view>
					<view class="day2">（每日24点清零）</view>
					<image class="circelimg" src="../../static/cloudBall/ballCircel.png"></image>
				</button>
			</view>
		</view>
	</view>
</template>

<script>
	// 浮动类型
	const CLOUDTYPE = [{
			type: 0,
			color: 'purple',
			txtCls: 'purple-txt',
			infoCls: 'purple-info',
			imgUrl: '../../static/cloudBall/purpleBall.png'
		},
		{
			type: 1,
			color: 'orange',
			txtCls: 'orange-txt',
			infoCls: 'orange-info',
			imgUrl: '../../static/cloudBall/orangeBall.png'
		},
		{
			type: 2,
			color: 'blue',
			txtCls: 'blue-txt',
			infoCls: 'blue-info',
			imgUrl: '../../static/cloudBall/blueBall.png'
		},
		{
			type: 3,
			color: 'fire',
			txtCls: 'fire-txt',
			infoCls: 'fire-info',
			imgUrl: '../../static/cloudBall/fireBall.png'
		},
		{
			type: 4,
			color: 'pink',
			txtCls: 'pink-txt',
			infoCls: 'pink-info',
			imgUrl: '../../static/cloudBall/pinkBall.png'
		}
	]

	// 浮动位置
	let CLOUDPOSITION = [
		[{
				left: 10,
				top: 0,
				css: 'left:10rpx; top:0rpx'
			},
			{
				left: 60,
				top: 0,
				css: 'left:60rpx; top:0rpx'
			},
			{
				left: 110,
				top: 0,
				css: 'left:110rpx; top:0rpx'
			},
		],
		[{
				left: 10,
				top: 150,
				css: 'left:10rpx; top:150rpx'
			},
			{
				left: 60,
				top: 150,
				css: 'left:60rpx; top:150rpx'
			},
			{
				left: 110,
				top: 150,
				css: 'left:110rpx; top:150rpx'
			},
		],
		[{
				left: 10,
				top: 300,
				css: 'left:10rpx; top:300rpx'
			},
			{
				left: 60,
				top: 300,
				css: 'left:60rpx; top:300rpx'
			},
			{
				left: 110,
				top: 300,
				css: 'left:110rpx; top:300rpx'
			},
		],
		[{
				right: 10,
				top: 0,
				css: 'right:0rpx; top:0rpx'
			},
			{
				right: 60,
				top: 0,
				css: 'right:60rpx; top:0rpx'
			},
			{
				right: 110,
				top: 0,
				css: 'right:110rpx; top:0rpx'
			},
		],
		[{
				right: 10,
				top: 150,
				css: 'right:10rpx; top:150rpx'
			},
			{
				right: 60,
				top: 150,
				css: 'right:60rpx; top:150rpx'
			},
			{
				right: 110,
				top: 150,
				css: 'right:110rpx; top:150rpx'
			},
		],
		[{
				right: 10,
				top: 300,
				css: 'right:10rpx; top:300rpx'
			},
			{
				right: 60,
				top: 300,
				css: 'right:60rpx; top:300rpx'
			},
			{
				right: 110,
				top: 300,
				css: 'right:110rpx; top:300rpx'
			},
		],
	]

	export default {
		data() {
			return {
				cloudBall: []
			};
		},
		onLoad() {
			let arr = [{
				type: 0,
				num: 2000,
				info: '任务奖励'
			}, {
				type: 1,
				num: 1000,
				info: '任务奖励'
			},{
				type: 2,
				num: 1000,
				info: '任务奖励'
			},{
				type: 3,
				num: 1000,
				info: '任务奖励'
			},{
				type: 4,
				num: 1000,
				info: '任务奖励'
			},{
				type: 4,
				num: 1000,
				info: '任务奖励'
			}]
			this.cloudBall = this.setPosition(arr)
		},
		onReady() {

		},
		methods: {
			// 洗牌（洗牌位置）
			shuffle(array) {
				let m = array.length,
					t, i;
				// 如果还剩有元素…
				while (m) {
					// 随机选取一个元素…
					i = Math.floor(Math.random() * m--);
					// 与当前元素进行交换
					t = array[m];
					array[m] = array[i];
					array[i] = t;
				}
				return array;
			},
			setPosition(arr) {
				if (arr.length === 0) {
					return []
				}
				let res = []
				CLOUDPOSITION = this.shuffle(CLOUDPOSITION)
				for (let i = 0; i < arr.length; i++) {
					// 当前cloud
					let cur = arr[i]
					// 6个区域位置的一个
					let posArr = CLOUDPOSITION[i]
					// 类型
					let curType = CLOUDTYPE.find(v => v.type === cur.type)
					// 区域位置的3个位置随机一个
					let randomPos = posArr[Math.floor((Math.random() * posArr.length))]
					cur = Object.assign({}, cur, {
						pos: randomPos.css
					}, { ...curType
					})
					res.push(cur)
				}
				console.log(res)
				return res
			},
			tapCloud(index, item) {
				console.log(index, item)
				item.hide = true
				this.cloudBall.splice(index, 1, item)
			},
			tapMain() {
				console.log('click the main')
			}
		},
	}
</script>

<style>
	/* 容器 */
	.index {
		width: 100%;
		height: auto;
		background: #f8f8f8;
		overflow-x: hidden;
	}

	.index-ball-con {
		width: 100%;
		height: 560rpx;
		position: relative;
		background: #fff;
		z-index: 11;
	}

	/* 背景图（如果需要的话） */
	.bgpic {
		width: 750rpx;
		height: 100%;
		position: relative;
		top: 0;
		left: 0;
		z-index: 0;
	}

	.bgpic image {
		width: 100%;
		height: 100%;
		position: absolute;
		left: 0;
		top: 0;
	}

	.index button {
		border: none;
		margin: 0;
		padding: 0;
		background: transparent;
		border-color: transparent;
	}

	.index button::after {
		border: none;
	}

	/* 浮动按钮 */
	.index .tree {
		width: 100rpx;
		height: 145rpx;
		margin: 0px;
		padding: 0px;
		position: absolute;
		color: rgb(220, 131, 236);
		text-align: center;
		animation: cloud 1.667s linear infinite;
		z-index: 99rpx;
	}

	/* 浮动图片 */
	.index .tree .ball {
		position: absolute;
		left: 0;
		top: 0;
		margin: 0;
		padding: 0;
		border-radius: 50%;
		width: 100rpx;
		height: 100rpx;
	}

	.index .tree .purple-txt {
		position: absolute;
		left: 50%;
		top: 23%;
		font-size: 36rpx;
		height: 36rpx;
		line-height: 36rpx;
		transform: translateX(-50%);
	}

	.index .tree .purple-info {
		width: 100%;
		position: absolute;
		left: 50%;
		bottom: 8rpx;
		transform: translateX(-50%);
		font-size: 20rpx;
		height: 20rpx;
		line-height: 20rpx;
	}

	.index .tree .orange-txt {
		position: absolute;
		left: 50%;
		top: 23%;
		font-size: 36rpx;
		color: #fe8752;
		height: 36rpx;
		line-height: 36rpx;
		transform: translateX(-50%);
	}

	.index .tree .orange-info {
		width: 100%;
		position: absolute;
		left: 50%;
		bottom: 8rpx;
		color: #fe8752;
		transform: translateX(-50%);
		font-size: 20rpx;
		height: 20rpx;
		line-height: 20rpx;
	}

	.index .tree .blue-txt {
		position: absolute;
		left: 50%;
		top: 23%;
		font-size: 36rpx;
		color: #6ea1f3;
		height: 36rpx;
		line-height: 36rpx;
		transform: translateX(-50%);
	}

	.index .tree .blue-info {
		width: 100%;
		position: absolute;
		left: 50%;
		bottom: 8rpx;
		color: #6ea1f3;
		transform: translateX(-50%);
		font-size: 20rpx;
		height: 20rpx;
		line-height: 20rpx;
	}

	.index .tree .fire-txt {
		position: absolute;
		left: 50%;
		top: 23%;
		font-size: 36rpx;
		color: #ff0000;
		height: 36rpx;
		line-height: 36rpx;
		transform: translateX(-50%);
	}

	.index .tree .fire-info {
		width: 100%;
		position: absolute;
		left: 50%;
		bottom: 8rpx;
		color: #ff0000;
		transform: translateX(-50%);
		font-size: 20rpx;
		height: 20rpx;
		line-height: 20rpx;
	}

	.index .tree .pink-txt {
		position: absolute;
		left: 50%;
		top: 23%;
		font-size: 36rpx;
		color: #ff0000;
		height: 36rpx;
		line-height: 36rpx;
		transform: translateX(-50%);
	}

	.index .tree .pink-info {
		width: 100%;
		position: absolute;
		left: 50%;
		bottom: 8rpx;
		color: #ff0000;
		transform: translateX(-50%);
		font-size: 20rpx;
		height: 20rpx;
		line-height: 20rpx;
	}

	/* 中间呼吸按钮 */
	.pushFormSubmit {
		width: 300rpx;
		height: 300rpx;
		position: absolute;
		top: 63rpx;
		left: 50%;
		transform: translateX(-50%);
	}

	.index .circel {
		width: 300rpx;
		height: 300rpx;
		border-radius: 50%;
		font-family: 'PingFang-SC-Regular';
		overflow: hidden;
		animation: circel 1.667s linear infinite;
	}

	@-webkit-keyframes circel {
		0% {
			transform: scale(1);
		}

		50% {
			transform: scale(1.12);
		}

		100% {
			transform: scale(1);
		}
	}

	@keyframes circel {
		0% {
			transform: scale(1);
		}

		50% {
			transform: scale(1.12);
		}

		100% {
			transform: scale(1);
		}
	}

	.index .circel .circelimg {
		position: absolute;
		width: 100%;
		height: 100%;
		left: 0;
		top: 0;
		z-index: 0;
		border-radius: 50%;
	}

	.index .circel view {
		position: absolute;
		left: 50%;
		z-index: 1;
		transform: translate(-50%);
	}

	.index .number {
		height: 70rpx;
		line-height: 70rpx;
		top: 107rpx;
		font-size: 70rpx;
		font-family: 'Roboto';
		font-weight: 400;
		color: rgba(255, 255, 255, 1);
	}

	.index .today {
		height: 20rpx;
		line-height: 20rpx;
		top: 80rpx;
		font-size: 20rpx;
		font-family: PingFang-SC-Regular;
		color: rgba(255, 255, 255, 0.8);
	}

	.index .day1 {
		height: 28rpx;
		line-height: 28rpx;
		top: 198rpx;
		font-size: 28rpx;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(255, 255, 255, 1);
	}

	.index .day2 {
		height: 16rpx;
		line-height: 16rpx;
		top: 238rpx;
		font-size: 16rpx;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(255, 255, 255, 1);
		opacity: 0.6;
	}

	.index .treehide {
		animation: hide 0.5s linear forwards 1;
	}

	@-webkit-keyframes cloud {
		0% {
			transform: translateY(0);
		}

		50% {
			transform: translateY(8rpx);
		}

		100% {
			transform: translateY(0);
		}
	}

	@keyframes cloud {
		0% {
			transform: translateY(0);
		}

		50% {
			transform: translateY(8rpx);
		}

		100% {
			transform: translateY(0);
		}
	}

	@-webkit-keyframes hide {
		0% {
			opacity: 1;
		}

		100% {
			opacity: 0;
		}
	}

	@keyframes hide {
		0% {
			opacity: 1;
		}

		100% {
			opacity: 0;
		}
	}
</style>
