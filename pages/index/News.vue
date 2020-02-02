<template>
	<view class="solid-bottom">
		<cu-custom class="solid-bottom" bgColor="bg-gray " :isBack="true"><block slot="backText">龙井人家</block></cu-custom>
		<view class="cu-chat ">
			<view class="cu-item ">
				<view class="cu-avatar radius"  style="background-image:url(../../static/input/形状4@3x.png);"></view>
				<view class="main">
					<view class="content shadow" style="font-size: 26upx;">
						<text>终于等到你啦，感谢您关注龙井人家。
						点击下方我的社区即可进入社区群聊哟~
						回复【公积金】在线查询公积金个人账户
						回复【落户】落户政策查询和办理
						回复【水电】停水/电地区查询
						回复【港澳】预约港澳通行证办理和续签
						回复【地铁】地铁路线查询和收班时间
						回复【社保】个人社保相关内容查询
						回复【升学】中小学对口划片范围查询
						回复【违章】违章查询和处理
						回复【居住证】居住证办理和进度查询
						回复【天气】最新天气预报
						回复【公租房】查询公租房新规
						回复【养犬】文明养犬规范和最新养犬政策
						回复【低保】低保申请流程和条件
						回复【退休】办理退休需要材料和流程
						</text>
					</view>
				</view>
			</view>
		</view>

		<view class="cu-bar foot input" :style="[{bottom:InputBottom+'px'}]">
			 <view class="solid-right" style="padding: 0 15upx 0 20upx;" @longpress="showModal" @tap="hideModal" data-target="Modal">
				<image src="../../static/input/键盘.png" mode="" style="width: 45upx; height: 45upx;" ></image>
			</view>
			<view class="foot flex justify-left cu-modal" :class="modalName=='Modal'?'show':''"  :style="[{bottom:InputBottom+'px'}]">
				<view class="action conmunity1"  >
					<text class="cuIcon-sound text-grey"></text>
				</view>
				<input class="solid-bottom conmunity1"  :adjust-position="false" :focus="false" maxlength="300" cursor-spacing="10"
				   @focus="InputFocus" @blur="InputBlur">
				</input>
				<view class="action conmunity1" >
					<text class="cuIcon-emojifill text-grey"></text>
				</view>
				<button class="cu-btn bg-red shadow conmunity1 margin-top-xs margin-right-xs" >发送</button>
			</view>
			<view class="conmunity2" @tap="goMore('/pages/index/index')">
				<button class="cu-btn bg-white text-black">我的社区</button>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				InputBottom: 0,
				modalName: null,
				modalName1: null,
			};
		},
		methods: {
			InputFocus(e) {
				this.InputBottom = e.detail.height
			},
			InputBlur(e) {
				this.InputBottom = 0
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
			showModal1(e) {
				this.modalName1 = e.currentTarget.dataset.target
			},
			hideModal1(e) {
				this.modalName1 = null
			},
		}
	}
</script>

<style>
page{
  padding-bottom: 100upx;
}

.conmunity2 button{
	width: 650upx;
	text-align: center;
}
.cu-modal {
	position: absolute;
	bottom: 0;
	left: 80upx;
	opacity: 0;
	outline: 0;
	text-align: center;
	-ms-transform: scale(1.185);
	transform: scale(1.185);
	backface-visibility: hidden;
	perspective: 2000upx;
	background: rgba(255, 255, 255, 1);
	transition: all 0.3s ease-in-out 0s;
	pointer-events: none;
}

.cu-modal::before {
	content: "\200B";
	display: inline-block;
	height: 100%;
	vertical-align: middle;
}

.cu-modal.show {
	opacity: 1;
	transition-duration: 0.3s;
	-ms-transform: scale(1);
	transform: scale(1);
	overflow-x: hidden;
	overflow-y: auto;
	pointer-events: auto;
}

.cu-dialog {
	position: relative;
	display: inline-block;
	vertical-align: middle;
	margin-left: auto;
	margin-right: auto;
	width: 80upx;
	max-width: 100%;
	background-color: #f8f8f8;
	border-radius: 10upx;
	overflow: hidden;
}

.cu-modal.bottom-modal::before {
	vertical-align: bottom;
}

.cu-modal.bottom-modal .cu-dialog {
	width: 100%;
	border-radius: 0;
}

.cu-modal.bottom-modal {
	margin-bottom: 0;
}

.cu-modal.bottom-modal.show {
	margin-bottom: 0;
}

.cu-modal.drawer-modal {
	transform: scale(1);
	display: flex;
}

.cu-modal.drawer-modal .cu-dialog {
	height: 100%;
	min-width: 200upx;
	border-radius: 0;
	margin: initial;
	transition-duration: 0.3s;
}

.cu-modal.drawer-modal.justify-start .cu-dialog {
	transform: translateX(-100%);
}

.cu-modal.drawer-modal.justify-end .cu-dialog {
	transform: translateX(100%);
}

.cu-modal.drawer-modal.show .cu-dialog {
	transform: translateX(0%);
}
.cu-modal .cu-dialog>.cu-bar:first-child .action{
  min-width: 100rpx;
  margin-right: 0;
  min-height: 100rpx;
}

</style>
