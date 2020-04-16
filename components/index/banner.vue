<template>
	<view>
		<swiper indicator-dots autoplay circular :interval="3000" :duration="800" :style="getStyle">
			<block v-for="(item,idx) in imageData" :key="idx">
				<swiper-item>
					<view class="swiper-item" @tap="handlerClick(item,idx)">
						<image lazy-load :src="item.src" :style="getStyle"></image>
					</view>
				</swiper-item>
			</block>
		</swiper>
	</view>
</template>

<script>
	export default {
		props: {
			imageData: {
				props: Array,
				default: () => []
			},
			height:{
				type:Number,
				default:350
			},
			preview:{
				type:Boolean,
				default:false
			}
		},
		data() {
			return {
			
			}
		},
		computed:{
			getStyle(){
				return `height: ${this.height}rpx;`
			},
			imgs(){
				return this.imageData.map(item=>item.src);
			}
		},
		methods: {
			handlerClick(data, index) {
				uni.previewImage({
					current:index,
					urls:this.imgs,
				})
			}
		}
	}
</script>

<style scoped>
	
</style>



