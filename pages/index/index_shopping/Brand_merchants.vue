<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')"  >
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red" >
					品牌商家
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view>
			<view class="text-white text-center text-bold">
				<view class="" style="height: 80upx;background-color: #ff637a;padding: 15upx;  font-size: 29upx;">店 铺 列 表</view>
			</view>
		</view>
		<view class="bg-white align-center flex justify-around solid-bottom" style="padding: 15upx;">
			<view class=""  style=""> 
				<view style="font-size: 28upx;">
				       <xfl-select 
				           :list="list1"
				           :clearable="false"
				           :showItemNum="5" 
				           :listShow="false"
				           :isCanInput="true"  
				           :style_Container="'height: 70upx; width:220upx;font-size: 28upx;'"
				           :placeholder = "'全部分类'"
				           :initValue="''"
				           :selectHideType="'hideAll'"
				       >
				       </xfl-select>
				</view>
			</view>
			
			<view class="">
				<view style="width: 220upx;font-size: 28upx;">
				       <xfl-select 
				           :list="list2"
				           :clearable="false"
				           :showItemNum="5" 
				           :listShow="false"
				           :isCanInput="true"  
				           :style_Container="'height: 70upx; width:220upx;font-size: 28upx;'"
				           :placeholder = "'街    道'"
				           :initValue="''"
				           :selectHideType="'hideAll'"
				       >
				       </xfl-select>
				</view>
			</view>
			<view class="">
				<view style="width: 220upx;font-size: 28upx;">
				       <xfl-select 
				           :listShow="false"
				           :isCanInput="true"  
				           :style_Container="'height: 70upx; width:220upx;font-size: 28upx;'"
				           :placeholder = "'离我最近'"
						    :selectHideType="'none'"
				       >
				       </xfl-select>
				</view>
			</view>
			<!-- <view class="img-align icon-ebae" @tap="tabSelect" style="border: #c0c4cd 2upx solid; width: 230upx; height: 70upx; line-height: 60upx;border-radius: 10upx;padding: 0 0 0 8upx;">
				<input class="input " :placeholder = "'离我最近'" placeholder-style="color: #000;" type="text" >
			</view> -->
		</view>
		
		<view class="cu-list menu-avatar">
			<view class="bg-white">
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_08.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								绿源超市大观楼店
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								超市
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">超</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">10.1km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_141.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								江语晨小区服务
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								果蔬粮油居家生活用品
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">零</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">13.1km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_20.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								正和金帝庄园服务站
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								小区生活服务
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">餐</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">13.6km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_38.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								愿君连锁
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								家电用气、日用百货
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">服</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">14.8km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_32.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								智慧水果
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								新鲜水果
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">鲜</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">16.2km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around" >
						<view>
							<image src="../../../static/input/社区商圈改_26.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
									廿四季线下连锁店
								</text>
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								<text class="">宜宾本地应季果蔬</text>
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">特</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">17.1km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_44.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;">
								金文鞋城总店
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								放心、实惠
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">通</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">17.5km</view>
					</view>
					
				</view>
				<view class="flex bg-white justify-between" @tap="goMore('/pages/index/index_shopping/shop_details')"  style="border-bottom: #DDDDDD 1upx solid;padding: 10upx;">
					<view class="mall_contents bg-white flex  justify-around">
						<view>
							<image src="../../../static/input/社区商圈改_44.png" mode="" style="width: 160upx; height: 120upx;"></image>
						</view>
						<view class="" style="line-height: 45upx; padding-left: 15upx;">
							<view class="text-cut text-black" style="font-size: 30upx;" >
								塞多电脑城
							</view>
							<view class="text-cut" style="font-size: 26upx;" >
								放心、实惠
							</view>
						</view>
					</view>
					<view>
						<view class="flex" style="height: 40upx;">
							<view class="bg-red margin-lr" style="padding: 0 8upx;">翠</view>
							<view class="bg-orange margin-right" style="padding: 0 8upx;">服</view>
						</view>
						<view class="text-right" style="margin: 40upx 30upx 0 0;">18.1km</view>
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
	import xflSelect from '../../../components/xfl-select/xfl-select-shop.vue'
	export default {
		data() {
			return {
				PageCur: 'Home',
				/* TabCur: 0,
				scrollLeft: 0, */
				list1: [ //全部分类
				    '超市',
				    '零售',
				    '餐饮',
				    '鲜香',
					'特惠',
					'通讯',
					'服务'
				],
				list2: [ //全部分类
				    '大安街道',
				    '凉高山街道',
				    '龙井街道',
				    '马冲口街道',
				],
			}
		},
		components: { xflSelect },  //注册为子组件
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
			
		}
	}
</script>

<style>
.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	padding: 0 10upx;
	display: flex;
	justify-content: space-between;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 10upx 5upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 235upx;
		height: 80upx;
		line-height: 80upx;
		text-align: center;
		border: #DDDDDD 1upx solid;
	}
.cu-item{
	 border-bottom: #DDDDDD solid 1upx;
}
.logo-list{
	width: 40upx;
	height: 30upx;
	margin: 10upx;
}
.count-logo{
	width: 45upx;
	height: 20upx;
	margin: 0 5upx;
}
.text-grey{
	position: absolute;
	right: 25upx;
	bottom: 10upx;
}
.zuo{
	width: 700upx;
}

.cu-list.menu-avatar>.pic-modle{
	height: 210upx;
}
.text-time{
	color: #AAAAAA;
}
.text-title{
	color: text-black;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 28upx;
}
</style>
