<template>
	<view :class="[customClass,'divider']"></view>
</template>

<script>
	export default {
		props:{
			customClass:{
				type:String,
				default:""
			}			
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style>
.divider{
	height:18upx;
	background:#f5f5f5;
}
</style>
