<template>
	<view>
		<view class="d-flex border-top border-bottom">
			<view class="col-3 d-flex a-center j-center py-2 font-md" v-for="(item,index) in list" :key="item.name" @tap="changeScreen(index)">
				<text :class="[currentIndex == index ? 'main-text-color' : 'text-secondary']">{{item.name}}</text>
				<view class="d-flex flex-column">
					<view class="line-h0 icon iconfont icon-paixu-shengxu" :class="[item.status == 1 ? 'main-text-color' : 'text-light-muted' ]"></view>
					<view class="line-h0 icon iconfont icon-paixu-jiangxu" :class="[item.status == 2 ? 'main-text-color' : 'text-light-muted' ]"></view>
				</view>
			</view>
			<view class="col-3 d-flex a-center j-center py-2 font-md main-text-color" @tap="openDraw">
				<text>筛选</text>
			</view>
		</view>
		<block v-for="(item,index) in searchList" :key="index">
			<view class="row border-bottom line-h0 border-light-secondary p-2 animated fadeIn faster "
			@tap="openDetail">
				<view class="span-7 line-h d-flex">
					<image 
					class="rounded"
					style="width: 100%;height: 100%;" 
					:src="item.titlepic" 
					mode="widthFix"></image>
				</view>
				<view class="span-13 line-h p-1 pl-3 d-flex flex-column j-sb">
					<view>
						<view class="text-dark" style="font-size: 36upx;font-weight: 650;">
							{{item.title}}
						</view>
						<view class="text-secondary font line-h-sm">
							{{item.desc}}
						</view>
					</view>
					<view>
						<view class="d-flex main-text-color line-h font-weight mb-1"
						style="font-size: 35upx;">
							<view class="font a-self-start line-h font-weight-100">￥</view>
							{{item.pprice}}
						</view>
						<view class="d-flex text-secondary font">
							<text class="mr-1">{{item.comment_num}} 条评论</text>
							<text>{{item.good_num}} 满意</text>
						</view>
					</view>
				</view>
			</view>
		</block>
		<uni-drawer :visible="visible" mode="right" @open="visible=true" @close="visible=false">
		    <view style="padding:30rpx;">
		        <view class="uni-title">抽屉式导航</view>
		    </view>
			<view class="d-flex position-fixed bottom-0 right-0 border-top border-light" style="width: 100%;">
				<view class="flex-1 font-md py-2 text-center bg-light-secondary" @tap.stop="reset">重置</view>
				<view class="flex-1 font-md py-2 text-center text-white main-bg-color" @tap.stop="submit">确定</view>
			</view>
		</uni-drawer>
	</view>
</template>

<script>
	import uniDrawer from '@/components/uni-ui/uni-drawer/uni-drawer.vue'
	export default {
		 components: {uniDrawer},
		data() {
			return {
				currentIndex:0,
				visible:false,
				searchList:[
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					},
					{
						id:12,
						titlepic:"/static/images/demo/list/1.jpg",
						title:"真无限蓝牙耳机",
						desc:"雅致简约 / 分体式入耳 / 收纳盒充电 / 蓝牙5.0 / 触控操作",
						pprice:199,
						comment_num:1348,
						good_num:'98%'
					}
				],
				list:[
					{name:'综合',status:1},
					{name:'销量',status:0},
					{name:'价格',status:0}
				]				
			}
		},
		onNavigationBarSearchInputChanged(e){
			console.log('tap',e);
		},
		onNavigationBarButtonTap(){
			console.log('button click')
		},
		onLoad(options){
		},
		onPullDownRefresh() {
			//监听下拉刷新动作的执行方法，每次手动下拉刷新都会执行一次
			console.log('refresh');
			setTimeout(function () {
				uni.stopPullDownRefresh();  //停止下拉刷新动画
			}, 1000);
		},
		onBackPress() {
			if(this.visible){
				this.visible=false;
				return true;
			}
		},
		methods: {
			openDetail(){
				uni.navigateTo({
					url:'../detail/detail'
				})
			},
			openDraw(){
				console.log('open')
				this.visible=true;
			},
			reset(){
				
			},
			submit(){
				this.visible=false;
			},
			changeScreen(index){
				let oldIndex=this.currentIndex;
				let oldItem=this.list[oldIndex];
				if(oldIndex == index){
					oldItem.status =  oldItem.status == 1 ? 2 : 1;
					return;
				}
				this.currentIndex=index;
				oldItem.status=0;
				this.list[index].status=1;
			}
		}
	}
</script>

<style>

</style>
