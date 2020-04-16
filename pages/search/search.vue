<template>
	<view>
		<card title="热门搜索" cover="/static/images/demo/search-banner.png"></card>
		
		<card title="常用分类" :bodyPadding="true" :headBorderBottom="false">
			<colorTag :list="list"></colorTag>
		</card>
		<template >
			<divider />
			<card title="搜索记录" v-if="historyList.length">
				<view slot="right" class="font text-primary"
				@click="clearHistory">清除搜索记录</view>
				<uni-list-item v-for="(item,index) in historyList" :key="index" 
				:title="item" :showArrow="false" @click="quickSearch(item)"></uni-list-item>
			</card>
		</template>
	</view>
</template>

<script>
	import card from '@/components/common/card.vue';
	import colorTag from '@/components/common/colorTag.vue';
	import uniListItem from "@/components/uni-ui/uni-list-item/uni-list-item.vue"
	export default {
		components:{
			card,
			colorTag,
			uniListItem
		},
		data() {
			return {
				historyList:['测试'],
				list:[
					{ name:'耳机' },
					{ name:'手机' },
					{ name:'音箱' },
					{ name:'手表' },
					{ name:'配件' },
					{ name:'网关/传感器' },
					{ name:'健康' },
					{ name:'酷玩' },
				]
			}
		},
		methods: {
			quickSearch(name){
				uni.navigateTo({
					url:`../search-list/search-list?name=${name}`
				})
			},
			clearHistory(){
				uni.showModal({
					title: '提示',
					content: '是否要清除搜索历史？',
					cancelText: '取消',
					confirmText: '清除',
					success: res => {
						if (res.confirm) {
							uni.removeStorageSync('searchHistory');
							this.historyList = []
						}
					},
				});
			}
		}
	}
</script>

<style>

</style>
