<template>
	<view>
		
		
		<view class="px-3 py-2">
			<swiper-dot :info="swipers" :current="current"> 
			<swiper :current="current" circular :autoplay="true" :interval="3000" :duration="150"
			 style="height: 250rpx;" @change="changeSwiper">
				<swiper-item  v-for="(item,index) in swipers" :key="index" >
					
					<image  :src="item.src" mode="aspectFill"
					 style="height: 250rpx; width: 100%;"
					 class="rounded-lg"
					 ></image>
					
				</swiper-item>
			</swiper>
			
			</swiper-dot>
			
		
			</view>

			<card title="为你推荐">
			
			<view class="f-list">
				<view v-for="i in 6":key="i" class="rounded-lg border mb-2" style="margin-left: 15rpx; margin-right: 15rpx; min-height: 5rpx; 
				width: 328rpx; position: relative;" @click="openDeatailVedio()">
				<image src="/static/demo/list2/1.jpg" style="height: 220rpx ; width: 100%;" class="rounded-top-lg"></image>	
				<view class="text-white flex align-center" style="height: 65rpx; background-image: 
				linear-gradient(to bottom, rgba(0,0,0,0),rgba(0,0,0,0.8)); position: absolute;left: 0; right: 0;
				 top: 155rpx;">
					<text class="iconfont iconbofangshu mx-1 font-md"></text>
					<text class="font-sm">203万</text>
					<text class="iconfont iconbofang font-md"></text>
					<text class="font-sm">5910</text>
				</view>
				<view class=" px-1 pb-1">		
				<view class="font">
					标题
				</view>
				<view class="flex align-center justify-between text-light-muted">
					<text class="font">恶搞</text>
					<text class="iconfont icongengduo"></text>
				</view>
				</view>
				</view>
			</view>
			
			</card>
			<view class="f-divider">
				
			</view>
			
			<card title="为你推荐">
			<view class="f-list">
				<view v-for="i in 6" :key="i" class="rounded-lg mb-2" style="margin-left: 15rpx; margin-right: 15rpx; min-height: 5rpx; 
				width: 210rpx; position: relative;">
				<image src="/static/demo/list3//1.webp" style="height: 280rpx ; width: 100%;" class="rounded-lg"></image>	
				<view class="text-white flex align-center rounded-bottom-lg" style="height: 65rpx; background-image: 
				linear-gradient(to bottom, rgba(0,0,0,0),rgba(0,0,0,0.8)); position: absolute;left: 0; right: 0;
				 top: 215rpx;">
					<text class="iconfont iconbofangshu mx-1 font-md"></text>
					<text class="font-sm">203万</text>
					
				
				</view>
				<view class="font">		
		
					标题
				
				
				</view>
				</view>
			</view>
			
			</card>
			
			
		<view class="f-divider">
			
		</view>
		
			<card title="为你推荐">
			<view class="f-list">
				<media-List v-for="(item,index) in list3" :key="index" 
				:item="item" 
				:index="index" >
				</media-List>
			</view>
			</card>
	</view>
</template>

<script>
	 import swiperDot from "@/component/common/swiper-dot.vue"
	 import card from "@/component/common/card.vue"
	 import mediaList from "@/component/common/media-list.vue"
 	export default {
		components:{
			swiperDot,
			card,
			mediaList
		},
		data() {
			return {
				current:0,
				swipers:[{
					src:"/static/demo/swiper/1.jpg",
					title:"仿制b站1"
				},{
					src:"/static/demo/swiper/2.jpg",
					title:"仿制b站2"
				},{
					src:"/static/demo/swiper/3.jpg",
					title:"仿制b站3"
				}],
				list3:[{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app实战",
					create_time:"今天六点",
					paly_count:0,
					danmu_count:0
				}]
			}
		},
		onLoad() {

		},
		onNavigationBarSearchInputClicked() {
			console.log('点击了搜索框')
		},
		onNavigationBarButtonTap() {
			console.log('点击了按钮')
		},
		methods: {
         changeSwiper(e){
			 this.current  = e.detail.current
		 },
		 openDeatailVedio()
		 {
			 uni.navigateTo({
			 	url:"/pages/detail-video/detail-video"
			 })
		 }
		}
	}
</script>

<style>
 .f-list{
	 display: flex;
	 flex-wrap: wrap;
	 padding-left: 15rpx;
	 padding-right: 15rpx;
 }
</style>
