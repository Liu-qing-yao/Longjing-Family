<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action"  @tap="goMore('/pages/index/index_longjing/index_Alliance')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					党建地图
				</view>
				<view class="action">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
			
		</view>
		 <view class="page-body">
		        <view class="page-section page-section-gap">
		            <map style="width: 100%; height: 800px;" :latitude="latitude" :longitude="longitude" :markers="covers"  @markertap="showModal" data-target="Modal" ></map>
					<view>
						<view class="cu-modal" :class="modalName=='Modal'?'show':''">
							<view class="cu-dialog">
								<view class="cu-bar bg-white justify-end">
									<view class="content text-red">党委会</view>
									<view class="action" @tap="hideModal">
										<text class="cuIcon-close text-red"></text>
									</view>
								</view>
								<view class="solid-bottom solid-top" style="text-align: left; padding: 10upx 25upx; line-height: 50upx;">
									<view>名称：龙井街道党委会</view>
									<view>联系方式：12132244</view>
									<view>联系地址：翠屏区宜宾学院48408号</view>
									<view class="text-blue">[查看详细地址]</view>
								</view>
								<view class="flex justify-around solid-bottom">
									<view class="solid-right padding-right padding-tb-sm">
										<image src="../../../static/input/椭圆703.png" mode="" style="width: 40upx; height: 30upx;"></image>
										在附近找
									</view>
									<view class="solid-right padding-right padding-tb-sm">
										<image src="../../../static/input/椭圆713.png" mode="" style="width: 20upx; height: 30upx;"></image>
										到这里去
									</view>
									<view class="padding-right padding-tb-sm">
										<image src="../../../static/input/椭圆713拷贝.png" mode="" style="width: 20upx; height: 30upx;"></image>
										从这里出发
									</view>
								</view>
								<view>
									<view class=''>
										<view class='header bg-ff row padding flex justify-between'>
											<input class="uni-input" focus placeholder='请输入地址'></input>
											<button class="cu-btn bg-gradual-red text-white" style="width: 150upx; margin-left: 10upx;">搜索</button>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
					<view class="arrow-trans" style="position:fixed; top:600upx; right:-10upx;">
						<image class="" src="../../../static/input/地图箭头.png" mode=""  
							@tap="showModal" data-target="DrawerModalR" style="width: 60upx; height: 120upx;"></image>
					</view>
		        </view>
		 </view>
		<view>
			<view class="cu-modal drawer-modal justify-end " :class="modalName=='DrawerModalR'?'show':''" >
				<view class="arrow-trans2" style="position:fixed; top:600upx; left: 256upx;">
					<image class="" src="../../../static/input/地图箭头1.png" mode=""  
						@tap="hideModal" data-target="DrawerModalR" style="width: 60upx; height: 120upx;"></image>
				</view>
				<view class="cu-dialog basis-lg " @tap.stop="" :style="[{top:CustomBar+'px',height:'calc(80vh - ' + CustomBar + 'px)'}]">
					<view class="cu-list menu text-left ">
						<view class="text-white bg-red text-center padding-tb-sm " style="font-size: 34upx;">党建阵地列表</view>
						<uni-collapse accordion="true">
						    <uni-collapse-item title="大安街道办事处" style="background-color: #fe9148; color: #ffffff;">
						        <view class="solid-top bg-white" @tap="showModalL" data-target="DrawerModalL"  style="padding: 20upx 30upx;">
						            1.华大社区
									<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						        </view>
								<view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
								    2.大楻桶社区
									<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
								</view>
								<view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
								    3.广华社区
									<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
								</view>
								<view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
								    4.红苕地社区
									<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
								</view>
						    </uni-collapse-item>
						    <uni-collapse-item title="凉高山街道办事处" style="background-color: #fe9148; color: #ffffff;">
						       <view class="solid-top bg-white" @tap="showModalL" data-target="DrawerModalL"  style="padding: 20upx 30upx;">
						           1.华大社区
						       	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						       </view>
						       <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						           2.大楻桶社区
						       	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						       </view>
						       <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						           3.广华社区
						       	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						       </view>
						       <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						           4.红苕地社区
						       	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						       </view>
						    </uni-collapse-item>
						    <uni-collapse-item title="龙井街道办事处" style="background-color: #fe9148; color: #ffffff;">
						        <view class="solid-top bg-white" @tap="showModalL" data-target="DrawerModalL"  style="padding: 20upx 30upx;">
						            1.华大社区
						        	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						        </view>
						        <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						            2.大楻桶社区
						        	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						        </view>
						        <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						            3.广华社区
						        	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						        </view>
						        <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
						            4.红苕地社区
						        	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
						        </view>
						    </uni-collapse-item>
							<uni-collapse-item title="马冲口街道办事处" style="background-color: #fe9148; color: #ffffff;">
							    <view class="solid-top bg-white" @tap="showModalL" data-target="DrawerModalL"  style="padding: 20upx 30upx;">
							        1.华大社区
							    	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
							    </view>
							    <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
							        2.大楻桶社区
							    	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
							    </view>
							    <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
							        3.广华社区
							    	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
							    </view>
							    <view class="bg-white solid-top" @tap="showModalL" data-target="DrawerModalL" style="padding: 20upx 30upx; ">
							        4.红苕地社区
							    	<view style="font-size: 20upx; padding: 10upx 20upx 0;">地址：华大社区888号</view>
							    </view>
							</uni-collapse-item>
						</uni-collapse>
					</view>
				</view>
			</view>
		</view>
		<view>
			<view class="cu-modal drawer-modal" :class="modalNameL=='DrawerModalL'?'show':''" @tap="hideModalL" >
				<image src="../../../static/input/介绍箭头1.png" mode="" style="width: 50upx; height: 126upx; position: fixed;left: -10upx; bottom: 101upx;"></image>
			</view>
			<view class="cu-modal cu-modal1 drawer-modal flex justify-start" :class="modalNameL=='DrawerModalL'?'show':''">
				
				<view class="cu-dialog basis-lg cu-modal1" @tap.stop="" :style="[{top:CustomBar+'px',height:'calc(16vh - ' + CustomBar + 'px)'}]" style="overflow: auto;">
					<view class="cu-list menu text-left" >
						<view class="text-white solid-right" style="background-color: #fe9148; font-size: 24upx;">
							<text>
								华大社区是四川省自贡大安区龙井街道下辖的社区，城乡分类代码为111，为主城区。
								区划代码为510304002014，居民身份证号码前6位为510304。邮政编码为643020，长途电话区号为0813 ，车牌号码为川C。
								华大社区与和大社区、红苕地社区、广华社区、大楻桶社区、龙井社区相邻。
							</text>
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
	import uniCollapse from '../../../components/uni-collapse/uni-collapse.vue'
	import uniCollapseItem from '../../../components/uni-collapse-item/uni-collapse-item.vue'
	export default {
		
	    data() {
	            return {
					PageCur: 'Home',
					
					CustomBar: this.CustomBar,
					modalName: null,
					modalNameL: null,
	                title: 'map',
	                latitude: 39.909,
	                longitude: 116.39742,
	                covers: [{
						width: 30,
						height: 30,
	                    latitude: 39.909,
	                    longitude: 116.39742,
	                    iconPath: '../../../static/input/椭圆678.png',
						id: 1,
	                },
					{
						width: 30,
						height: 30,
						latitude: 30,
						longitude: 116.39,
						iconPath: '../../../static/input/椭圆678.png',
						id: 2,
					}],
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
			hideModal(e) {
				this.modalName = null
			},
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModalL(e) {
				this.modalNameL = null
			},
			showModalL(e) {
				this.modalNameL = e.currentTarget.dataset.target
			},
	    },
		components: {
			uniCollapse,uniCollapseItem
		}
	}
</script>

<style>

.box{
	border-bottom: 1upx #DDDDDD solid;
}
.navfirst{
	border-bottom: 1upx #DDDDDD solid;
	text-align: center;
}
.navfirst_1{
		/* background: #5ddad4; */
		margin: 15upx 6upx;
		border-radius: 15upx;
		font-size: 30upx;
		width: 175upx;
		text-align: center;
		padding: 0;
		height: 85upx;
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
	width: 40upx;
	height: 20upx;
	margin: 0 5upx;
}
.uni-input{
	border-radius: 10upx;
	border: #b5b1b1 1upx solid;
	height: 60upx;
	width: 500upx;
	text-align: left;
	padding-left: 10upx;
}

.arrow-trans image {
            animation: myfirst 0.9s infinite;
}
@keyframes myfirst {
            0% {
                transform: translate(0upx, 0upx);
            }
            50% {
                transform: translate(-12upx, 0upx);
            }
            100% {
                transform: translate(0upx, 0upx);
            }
}

.arrow-trans2 image {
            animation: myfirst2 0.9s infinite;
}
@keyframes myfirst2 {
            0% {
                transform: translate(0upx, 0upx);
            }
            50% {
                transform: translate(-12upx, 0upx);
            }
            100% {
                transform: translate(0upx, 0upx);
            }
}

.cu-modal1{
	position: fixed;
	top: 1020upx;
	right: 0;
	bottom: 0upx;
	left: 21upx;
	z-index: 1110; 
	background: rgba(0, 0, 0, 0);
} 

</style>
