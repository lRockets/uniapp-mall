<template>
	<view class="content">		
		<scroll-view scroll-x="true" class="w-100  scroll-row flex-row" :scroll-into-view="scrollInto" :scroll-with-animation="true" >
			<view :id="`tab${index}`"  @click="swiperClick(index)" class="scroll-row-item px-3" :class="{'text-primary':tabIndex == index}" style="height:80upx;line-height:80upx;" v-for="(item,index) in tabs" :key="item.name">
				<text class="font-md" >{{item.name}}</text>
			</view>
		</scroll-view>
		<swiper :current="tabIndex" :style="{height:scrollHeight+'px'}" @change="changeSwiper" :duration="150">
			<swiper-item v-for="(list,index) in tabs" :key="list.name">
				
				<scroll-view scroll-y="true" :style="{height:scrollHeight+'px'}">
					<template v-if="index == 0">
						<view>
							<banner :imageData="swipers"></banner>
							<view class="row j-sb py-2 m-1">
								<block v-for="item in classList" :key="item.text">
									<view class="span-4 d-flex flex-column j-center a-center py-1">
										<image :src="item.src" mode="widthFix" class="image"></image>
										<text class="font-sm mt-1">{{item.text}}</text>
									</view>
								</block>			
							</view>
							<divider></divider>
							<view class="d-flex">
								<image lazy-load src="/static/images/demo/demo1.jpg" style="width:373upx;height:530upx;border-right:2upx solid #f5f5f5"></image>
								<view style="width:375upx;height:530upx;" class="d-flex j-sb flex-column">
									<image src="/static/images/demo/demo2.jpg" style="width:100%;height:264upx;border-bottom:2upx solid #f5f5f5" ></image>
									<image src="/static/images/demo/demo3.jpg" style="width:100%;height:264upx;" ></image>
								</view>
							</view>
							<divider></divider>
							<card title="每日精选" cover="/static/images/demo/demo4.jpg"></card>
							<commonList :listData="listData"></commonList>
						</view>
					</template>
					<template v-else>
						33333333333
					</template>
				</scroll-view>
			</swiper-item>
		</swiper>
		
	</view>
</template>

<script>
	import banner from '@/components/index/banner.vue';
	import card from '@/components/common/card.vue';
	import commonList from '@/components/index/common-list.vue';
	export default {
		components:{
			banner,
			card,
			commonList
		},
		data() {
			return {
				tabIndex:0,
				scrollInto:'',
				scrollHeight:400,
				tabs:[
					{name:'关注'},
					{name:'推荐'},
					{name:'体育'},
					{name:'财经'},
					{name:'娱乐'},
					{name:'军事'},
					{name:'搞笑'},
					{name:'奇葩'},
				],
				swipers:[
					{src:'https://img.alicdn.com/tps/i4/TB1u.7gzAL0gK0jSZFtSutQCXXa.jpg_q90_.webp'},
					{src:'https://img.alicdn.com/simba/img/TB1aIkGtFP7gK0jSZFjSuw5aXXa.jpg'},
				],
				listData:[
					{titlepic:'/static/images/demo/list/1.jpg',title:'新品发布',desc:'描述',price:2000,oprice:null},
					{titlepic:'/static/images/demo/list/2.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/3.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/4.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/5.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/6.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/1.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/2.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/3.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/4.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/5.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
					{titlepic:'/static/images/demo/list/6.jpg',title:'新品发布',desc:'描述',price:2000,oprice:2600},
				],
				classList:[
					{src:'/static/indexnav/1.png',text:'新品发布'},
					{src:'/static/indexnav/2.gif',text:'小米众筹'},
					{src:'/static/indexnav/3.gif',text:'以旧换新'},
					{src:'/static/indexnav/4.gif',text:'1分拼团'},
					{src:'/static/indexnav/5.gif',text:'超值特卖'},
					{src:'/static/indexnav/6.gif',text:'小米秒杀'},
					{src:'/static/indexnav/7.gif',text:'真心想要'},
					{src:'/static/indexnav/8.gif',text:'电视热卖'},
					{src:'/static/indexnav/9.gif',text:'家店热卖'},
					{src:'/static/indexnav/10.gif',text:'米粉卡'}
				]
			}
		},
		onNavigationBarSearchInputClicked(){
			uni.navigateTo({
				url:'../search/search'
			})
		},
		onLoad() {
			let that=this;
			uni.getSystemInfo({
				success(res) {
					that.scrollHeight=res.windowHeight-uni.upx2px(82);
				}
			});
			
			
		},
		methods: {
			onrefresh(event) {
				uni.showToast({
					title: "refresh",
					icon: "none"
				});
				this.refreshText = "正在刷新...";
				this.refreshing = true;
				setTimeout(() => {
					this.pullrefresh('down');
				}, 100);
			},
			loadData(){
				this.loadingShow=true;
				setTimeout(()=>{
					this.loadingShow=false;
				},5000)
			},
			pullrefresh(){
				this.refreshing = false;
			},
			onpullingdown(event) {
				if (this.refreshing) {
					return;
				}
				if (Math.abs(event.pullingDistance) > Math.abs(event.viewHeight)) {
					this.refreshText = "释放立即刷新";
				} else {
					this.refreshText = "下拉可以刷新";
				}
			},
			addData() {
			
			},
			swiperClick(index){
				if(this.tabIndex == index){
					return;
				}
				this.tabIndex=index;
				this.scrollInto=`tab${this.tabIndex}`
				
			},
			changeSwiper(e){
				this.swiperClick(e.detail.current);
			},
		}
	}
</script>

<style scoped>
	.image{
		width:60upx;
		height:60upx;
	}
	.active text{
		color:#FF3333;
	}
</style>
