<template>
	<view class="d-flex flex-wrap">
		<view class="col-6 pb-2 px animated fadeIn faster " @tap="openDetail" v-for="item in listData" :key="item.id">
			<image class="w-100" :src="item.titlepic" mode="widthFix"></image>
			<view class="font-md text-dark px-2">{{item.title}}</view>
			<view class="text-muted font px-2 line-h-md">{{item.desc}}</view>
			<view class="d-flex px-2 pt-2">
				<view class="font-md text-danger mr-1 line-h d-flex">
					<view class="line-h font-sm a-self-start">
						￥</view>
					{{item.price}}
				</view>
				<text class="font-sm text-muted a-self-end line-through" v-if="item.oprice">￥{{item.oprice}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			listData: Array
		},
		methods: {
			openDetail() {
				uni.navigateTo({
					url: '../../pages/detail/detail'
				});
			}
		},
	}
</script>

<style>
</style>
