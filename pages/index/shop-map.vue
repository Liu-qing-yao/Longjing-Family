<template>
	<view class='container'>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_shopping/index_shopping')">
					<image src="../../../static/input/健康驿站_06.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					商圈地图
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/益路有你_34.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		
		<!-- <view class='header bg-ff'>
			<view class='row padding border-b font-26'>
				<view class='padding-l' @click='addressSearch'>
					<icon class='icon_search' type='search' size='22' color='#666' />
				</view>
			</view>
		</view> -->
		<map id='map' style="width: 100%; height: 1100upx;" :show-location="map.showLocation" :longitude="map.longitude" :latitude="map.latitude"
		  :controls="map.controls" :markers="map.covers" @markertap="showModal" data-target="Modal" @regionchange='mapChange'>
			<!-- <cover-view class='icon-position' style="margin-top: 100px;"> -->
				<!-- <cover-image src="/static/icon_position.png" class="icon-img"></cover-image> -->
			<!-- </cover-view> -->
		</map>
		
		<view>
			<view class="cu-modal" :class="modalName=='Modal'?'show':''">
				<view class="cu-dialog">
					<view class="cu-bar bg-white justify-end">
						<view class="content text-red">商家信息</view>
						<view class="action" @tap="hideModal">
							<text class="cuIcon-close text-red"></text>
						</view>
					</view>
					<view class="solid-bottom solid-top" style="text-align: left; padding: 10upx 25upx; line-height: 50upx;">
						<view>名称：绿源超市大观楼店</view>
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
								<!-- {{address.address}} --><input class="uni-input" focus placeholder='请输入地址'></input>
								<button class="cu-btn bg-gradual-red text-white" style="width: 150upx; margin-left: 10upx;" @click='addressSearch'>搜索</button>
							</view>
							
						</view>
					</view>
				</view>
			</view>
		</view>
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
	const app = getApp()
	var QQMapWX = require('../../libs/qqmap-wx-jssdk.min.js')
	var qqmapsdk = new QQMapWX({
	  key: 'LXCBZ-NNIKD-UZ64F-H6AFI-UNJLH-OCFGE'
	})
	export default {
		data() {
			return {
				detail: '',
				PageCur: 'Home',
				CustomBar: this.CustomBar,
				modalName: null,
				map: {
					latitude: 39.909,
					longitude: 116.39742,
					showLocation: true,
					covers: [{
						width: 20,
						height: 30,
					    latitude: 39.909,
					    longitude: 116.39742,
					    iconPath: '../../static/input/背景拷贝.png',
						id: 'map',
					}
					],
					 iconPath: '../../static/input/背景拷贝.png',
					 controls: [{
						id: 'map',
						iconPath: '../../static/input/背景拷贝.png',
						position: { left: 1200, top: 1200, width: 40, height: 40},
						clickable: false
					}], 
				},
				list: [],
				oftenList: [],
				address: {
					title: '',
					address: ''
				},
				checked: 0,
				scrollTop: 0,
				mapStatus: 1 // 控制选择地址时 地图不加载附近列表
			}
		},
		created() {
			uni.setNavigationBarTitle({
				title: '搜索地址'
			})
		},
		onLoad() {
			let map = this.map
			// this.getWidthHeight(e => {
			// 	console.log(e);
			//   map.controls[0].position.top = e.height - 45
			//   map.controls[0].position.left = e.width/2 - 10
			//   this.setData({
			// 	map: map
			//   })
			// })
			
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
			RadioChange(e) {
				this.radio = e.detail.value
			},
			getAddress (){
			    let that = this
			    uni.getLocation({
			      type: 'gcj02',
			      success: function(res) {
			        console.log(res)
			        let map = that.data.map
			        map.longitude = res.longitude
			        map.latitude = res.latitude
			        that.getWidthHeight(e => {
			          map.controls[0].position.top = e.height / 2 - 35
			          map.controls[0].position.left = e.width / 2 - 20
			          that.setData({
			            map: map,
			            position: {
			              longitude: res.longitude,
			              latitude: res.latitude
			            }
			          })
			          that.getAddressList(1)
			        })
			      },
			    })
			  },
			  
			getWidthHeight (fn){
				var query = uni.createSelectorQuery()
				query.select('#map').boundingClientRect()
				query.exec(res => {
				  fn(res[0])
				})
			  },
			getAddressList(s = 0) {
				let that = this
				let position = that.position
				console.log(position)
				qqmapsdk.reverseGeocoder({
					location: {
						latitude: position.latitude,
						longitude: position.longitude
					},
					get_poi: 1,
					poi_options: "page_size=20;page_index=1",
					success: function(e) {
						if (s) {
							e.result.pois[0].select = 1
							that.setData({
								list: e.result.pois,
								address: e.result.pois[0],
								checked: 0
							})
						} else {
							that.setData({
								list: e.result.pois
							})
						}
						
						setTimeout(() => {
							console.log('************');
							that.scrollTop = 1
						}, 1000)
					},
					fail: err => {
						console.log(err)
					}
				})
			},
			mapChange(e) {
				let that = this
				console.log(this.mapStatus);
				clearTimeout(this.timer)
				this.timer = setTimeout(() => {
					if (e.type == 'end') {
						that.mapCtx = uni.createMapContext('map')
						that.mapCtx.getCenterLocation({
							success: res => {
								console.log(res)
								that.setData({
									position: {
										latitude: res.latitude,
										longitude: res.longitude
									}
								})
								if (that.mapStatus) { // 防止地图点击时 进行多次加载
									that.getAddressList(1)
								} else {
									that.mapStatus = 1
								}
							}
						})
					}
				}, 200)
				
			},
			bindAddress(index) {
				let list = this.list
				let map = this.map
				map.latitude = list[index].location.lat
				map.longitude = list[index].location.lng
				this.setData({
					map: map,
					checked: index,
					address: list[index],
					mapStatus: 0
				})
			},
			setData(obj){
				Object.assign(this, obj)
			},
			addressSearch() {
				uni.navigateTo({
					url: '/pages/address-search/address-search'
				})
			},
			submit() {
				let that = this
				let detail = that.detail || ''
				let address = that.address
				let a = {
					address: address.title + detail,
					lat: address.location.lat,
					lng: address.location.lng
				}
				console.log(address, a)
			}
		}
	}
</script>

<style lang="scss">
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
	/**app.wxss**/
	/* page, view, scroll-view, swiper, block, icon, text, rich-text, button, input, label, picker, picker-view, slider, textarea, navigator, image, video, map, video{margin: 0; padding: 0; box-sizing: border-box;}
	
	page{background: #F6F6F6;font-size: 32rpx;}
	image{display: block;} */
	
	.item, .item-forward{background: #fff;padding: 25rpx 90rpx 25rpx 25rpx;position: relative;line-height: 46rpx;}
	.item-forward::before{content: '';width: 20rpx;height: 20rpx;border-top: 2px solid #a9a9a9;border-right: 2px solid #a9a9a9;border-radius: 2px;position: absolute;top: 50%;right: 35rpx;transform: rotate(45deg) translateY(-50%);}
	.item image, .item-forward image{width: 46rpx;height: 46rpx;display: block;margin-right: 10rpx;position: relative;}
	.active{background: #eee;}
	
	.row, .item, .item-forward, .coupons{display: flex;width: 100%;}
	.row-wrap{flex-wrap: wrap;}
	.col, .coupons .left{flex: 1;display: block;width: 100%;}
	.col-center{height: 100%;display: flex;align-items: center;}
	.float-r{float: right;}
	.padding{padding: 20rpx 25rpx;}
	.padding-t{padding-top: 20rpx;}
	.padding-b{padding-bottom: 20rpx;}
	.padding-l{padding-left: 25rpx;}
	.padding-r{padding-right: 25rpx;}
	.padding-tb{padding-top: 20rpx;padding-bottom: 20rpx;}
	.padding-lr{padding-left: 25rpx;padding-right: 25rpx;}
	.margin{margin: 20rpx 25rpx;}
	.margin-t{margin-top: 20rpx;}
	.margin-b{margin-bottom: 20rpx;}
	.margin-tb{margin-top: 20rpx;margin-bottom: 20rpx;}
	.margin-lr{margin-left: 25rpx;margin-right: 25rpx;}
	.border, .border-t, .border-r, .border-b, .border-l{position: relative;}
	.border{border: .5px solid #eee;}
	.border-t::after, .border-r::after, .border-b::after, .border-l::after{content: '';position: absolute;/*background: #eee;*/background: linear-gradient(to top, #eee .7px, transparent .7px);}
	.border-t::after, .border-b::after{height: 1px;left: 25rpx;right: 25rpx;top: 0;}
	.border-b::after{top: auto;bottom: 0;}
	.border-l::after, .border-r::after{width: 1px;top: 0;bottom: 0;left: 0;background: linear-gradient(to right, #eee .7px, transparent .7px);}
	.border-r::after{left: auto;right: 0;}
	.ellipsis-1{overflow: hidden;text-overflow: ellipsis;white-space: nowrap;}
	.bg{background: #E74246;}
	.bg-ff{background: #fff;}
	.color{color: #E74246;}
	.color-00{color: #000;}
	.color-ff{color: #fff;}
	.color-99, .icon_img_tip{color: #999;}
	.color-6c{color: #6c6c6c;} 
	.text-right{text-align: right;}
	.font-26{font-size: 26rpx;}
	
	.position-r{position: relative;}

	page {
		position: relative;
	}

	.map, map {
		width: 100%;
		height: 1200upx;
		/* position: fixed;
		left: 0;
		top: 100px;
		right: 0;
		bottom: 210px; */
	}
	.map{display: flex;align-items: center;justify-content: center;}

	.icon_search {
		margin-top: 20rpx;
	}

	.btn {
		line-height: 25px;
		border-radius: 4rpx;
		margin-top: -5rpx;
	}
	.footer {
		position: fixed;
		left: 0;
		right: 0;
		bottom: 0;
		/* height: 210px; */
	}

	.foot-border {
		border-bottom: 1px solid #eee;
		line-height: 32rpx;
	}

	.foot-border .padding {
		padding: 25rpx;
	}

	.foot-active {
		color: #E74246;
		position: relative;
	}

	.foot-active::after {
		content: '';
		position: absolute;
		height: 2px;
		background: #E74246;
		border-radius: 2px;
		bottom: 0;
		width: 5em;
		left: 50%;
		transform: translateX(-50%);
	}

	.scroll {
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
	}

	.scroll .padding {
		padding-right: 40px;
	}

	.scroll .icon_circle {
		position: absolute;
		right: 25rpx;
		top: 50%;
		transform: translateY(-50%);
	}

	.icon_img_tip {
		padding: 20rpx 0;
	}
	.icon-position{
		position: relative;top: 50%;left: 50%;width: 36px;height: 36px;transform: translate(-50%, -50%);
		.icon-img{width: 36px;height: 36px;display: block;position: fixed;top: 100px;left: 100px;}
	}
	.icon-img{width: 36px;height: 36px;display: block;position: fixed;top: 50%;left: 50%;transform: translate(-50%, -50%);margin-top: -70px;}
</style>
