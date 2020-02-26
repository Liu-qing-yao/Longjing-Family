<template>
	<view :class="[circle === true || circle === 'true' ? 'uni-fav--circle' : '']" :style="[{ backgroundColor: checked ? bgColorChecked : bgColor }]"
	 @click="onClick" class="uni-fav">
		<!-- #ifdef MP-ALIPAY -->
		<view class="uni-fav-star align-center" v-if="!checked && (star === true || star === 'true')">
			<uni-icons :color="fgColor" :style="{color: checked ? fgColorChecked : fgColor}" size="16" type="star-filled" />
		</view>
		<!-- #endif -->
		<!-- #ifndef MP-ALIPAY -->
		<uni-icons :color="fgColor" :style="{color: checked ? fgColorChecked : fgColor}" class="uni-fav-star" size="16" type="star-filled"
		 v-if="!checked && (star === true || star === 'true')" />
		<!-- #endif -->
		<text :style="{color: checked ? fgColorChecked : fgColor}" class="uni-fav-text  margin-left">{{ checked ? contentText.contentFav : contentText.contentDefault }}</text>
	</view>
</template>

<script>
	import uniIcons from "../uni-icons/uni-icons.vue";
	export default {
		name: "UniFav",
		components: {
			uniIcons
		},
		props: {
			star: {
				type: [Boolean, String],
				default: true
			},
			bgColor: {
				type: String,
				default: "#eeeeee"
			},
			fgColor: {
				type: String,
				default: "#666666"
			},
			bgColorChecked: {
				type: String,
				default: "#007aff"
			},
			fgColorChecked: {
				type: String,
				default: "#FFFFFF"
			},
			circle: {
				type: [Boolean, String],
				default: false
			},
			checked: {
				type: Boolean,
				default: false
			},
			contentText: {
				type: Object,
				default () {
					return {
						contentDefault: "收藏",
						contentFav: "已收藏",
					};
				}
			}
		},
		watch: {
			checked() {
				if (uni.report) {
					if (this.checked) {
						uni.report("收藏", "收藏");
					} else {
						uni.report("取消收藏", "取消收藏");
					}
				}
			}
		},
		methods: {
			onClick() {
				this.$emit("click");
			}
		}
	};
</script>

<style lang="scss" scoped>
	$fav-height: 25px;

	.uni-fav {
		/* #ifndef APP-NVUE */
		display: flex;
		justify-content: center;
		/* #endif */
	/* 	flex-direction: row; */
		width: 110upx;
		height: $fav-height;
		line-height: $fav-height;
		border-radius: 3px;
		margin: 0;
		padding: 0;
	}

	.uni-fav--circle {
		border-radius: 30px;
	}

	.uni-fav-star {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		height: $fav-height;
		/* line-height: 24px; */
		/* margin-right: 3px; */
		margin: 0 7upx;


	}

	.uni-fav-text {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		height: $fav-height;
		/* line-height: $fav-height; */
		font-size: 26upx;
		margin: 0;
		padding: 0;
	}
</style>
