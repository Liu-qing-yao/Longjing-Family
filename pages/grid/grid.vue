<template>
	<view>
		<zy-grid :grid-list=gridList :show-tip="true" :col="4"></zy-grid>
	</view>
</template>

<script>
	import zyGrid from '../../components/zy-grid/zy-grid.vue'
	export default {
		components:{
			zyGrid
		},
		data () {
			return {
				gridList: [	//格子数据列表
					{
						name: '测试图标',
						imgUrl: '../../static/model/龙井之窗.png',
						tips: 19
					},
					{
						name: '测试图标',
						imgUrl: '../../static/model/玩味生活.png',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/model/民呼我应.png',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/model/益路有你.png',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/model/健康驿站.png',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/model/社区商圈.png',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-07.svg',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-08.svg',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-09.svg',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-10.svg',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-11.svg',
						tips: ''
					},
					{
						name: '测试图标',
						imgUrl: '../../static/zy-grid/grid-12.svg',
						tips: ''
					}
				]
			}
		}
	}
</script>

<style>
	
</style>
