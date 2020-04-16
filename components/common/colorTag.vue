<template>
	<view>
		<view class="px-2 py-1 border d-inline-block m-1" v-for="(item,index) in list" :key="index" :style="{'background-color':background[index%borderColor.length],'border-color':borderColor[index%borderColor.length]}">
			{{item.name}}
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			list: {
				type: Array,
				default: () => []
			},
			color: {
				type: Boolean,
				default: true
			}
		},
		data() {
			return {
				borderColor: ['#EEA6AA', '#DD6A4B', '#98D5D8', '#9DBE93', '#BCCD99'],
				background: ['#F8EAE9', '#FFBEC6', '#E8F6F6', '#E4F5E2', '#F2F6E8']
			}
		},
		computed: {},
	}
</script>

<style>
</style>
