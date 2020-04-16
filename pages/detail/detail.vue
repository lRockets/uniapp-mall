<template>
	<view>
		<banner :imageData="imgData" :height="750" :preview="true"></banner>
		<view class="p-2">
			<view class="font-lg">小米米家滤水壶滤芯三支装</view>
			<view class="font text-light-muted mb-2">高效过滤，享安心好水 / 有效滤除余氯，减少水垢、重金属等有害物质 / 360°进水流道设计 / 甄选优质滤材，保证过滤效果,高效过滤，享安心好水 / 有效滤除余氯，减少水垢、重金属等有害物质 / 360°进水流道设计 / 甄选优质滤材，保证过滤效果</view>
			<price>222</price>

			<scroll-view scroll-x class="scroll-row mt-2">
				<view class="scroll-row-item" style="width: 140upx;height: 110upx;" v-for="(item,index) in baseAttrs" :key="index">
					<view class="d-flex flex-column a-center j-center">
						<view class="iconfont line-h-sm" :class="item.icon"></view>
						<view class="line-h-sm">{{item.title}}</view>
						<view class="text-light-muted font-sm line-h-sm pb-2 text-ellipsis text-center" style="width:140upx;">
							{{item.desc}}
						</view>
					</view>
				</view>
			</scroll-view>
			
			<view class="p-2 mt-3">
				<view class="rounded bg-light-secondary">
					<uni-list-item @click="show('attr')"
					v-if="detail.sku_type === 1" showArrow>
						<view class="d-flex">
							<text class="mr-2 text-muted">已选</text>
							<text>{{checkedSkus}}</text>
						</view>
					</uni-list-item>
					<uni-list-item @click="goToCoupon" showArrow>
						<view class="d-flex">
							<text class="mr-2 text-muted">优惠券</text>
							<text class="main-text-color">马上领取</text>
						</view>
					</uni-list-item>
					<uni-list-item @click="show('express')">
						<view class="d-flex">
							<text class="mr-2 text-muted">配送</text>
							<text class="mr-2">北京 东城区</text>
							<text class="main-text-color">现配</text>
						</view>
					</uni-list-item>
					<uni-list-item extraWidth="3%" @click="show('service')">
						<view class="d-flex a-center">
							<view class="text-muted font-sm d-flex a-center mr-1">
								<view class="iconfont icon-finish main-text-color"></view>
								小米自营
							</view>
							<view class="text-muted font-sm d-flex a-center mr-1">
								<view class="iconfont icon-finish main-text-color"></view>
								小米发货
							</view>
							<view class="text-muted font-sm d-flex a-center mr-1">
								<view class="iconfont icon-finish main-text-color"></view>
								七天无理由退货
							</view>
						</view>
					</uni-list-item>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item';
	import banner from '@/components/index/banner.vue';
	import price from '@/components/common/price.vue';
	export default {
		components: {
			banner,
			price,
			uniListItem
		},
		computed:{
			// 选中的sku
			checkedSkus(){
				// 拿到选中skus组成字符串
				let checkedSkus = this.selects.map(v=>{
					return v.list[v.selected].name
				})
				return checkedSkus.join(',')
			},
			// 选中skus的索引
			checkedSkusIndex(){
				if (!Array.isArray(this.detail.goodsSkus)) {
					return -1
				}
				let index = this.detail.goodsSkus.findIndex((item)=>{
					return item.skusText === this.checkedSkus
				})
				return index
			},
		},
		data() {
			return {
				imgData: [{
						src: '//cdn.cnbj0.fds.api.mi-img.com/b2c-mimall-media/1f139d4725a17eb23d99c1783e113839.jpg'
					},
					{
						src: 'http://m.360buyimg.com/mobilecms/s720x720_jfs/t1/75843/13/5247/178613/5d36c187E0274fdde/2f63d53828761609.jpg!q70.dpg.webp'
					}
				],
				detail:{
					id:20,
					title:"小米MIX3 6GB+128GB",
					desc:"磁动力滑盖全面屏 / 前后旗舰AI双摄 / 四曲面彩色陶瓷机身 / 高效10W无线充电",
					cover:"/static/images/demo/list/1.jpg",
					pprice:3299,
					num:1,
					max:100
				},
				baseAttrs: [{
					icon: "icon-cpu",
					title: 'CPU',
					desc: '骁龙765G',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '四摄像头',
					desc: '6400万+800万+500万+200万像素',
				},{
					icon: "icon-cpu",
					title: '超大屏',
					desc: '6.67英寸',
				},{
					icon: "icon-cpu",
					title: '小米自营',
					desc: '小米发货',
				},{
					icon: "icon-cpu",
					title: '小米自营',
					desc: '小米发货',
				}]
			}
		},
		methods: {
			goToCoupon(){
				uni.navigateTo({
					url: '../coupon/coupon',
				});
			},
			show(){
				
			}
		}
	}
</script>

<style>

</style>
