<template>
	<view class="card">
		<view v-if="cardHead"  :class="{'border-bottom':headBorderBottom}" class="p-2 main-border-color j-sb d-flex">
			<text class="font-md font-weight">{{title}}</text>
			<slot name="right"></slot>
		</view>
		<view :class="{'p-2' : bodyPadding}">
			<image v-if="cover" :src="cover" mode="widthFix" style="width:100%;"></image>
			<slot></slot>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			cardHead:{
				type:Boolean,
				default:true
			},
			// 是否给body加padding
			bodyPadding:{
				type:Boolean,
				default:false
			},
			title:{
				type:String,
				default:''
			},
			cover:{
				type:String,
				default:''
			},
			headBorderBottom:{
				type:Boolean,
				default:true
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style>

</style>
