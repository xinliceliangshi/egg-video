<template>
<view>
	<view v-for="(item,index) in list" :key="index">
		<media-List 
		:item="item" 
		:index="index" >
		</media-List>
		<view class="flex" style="height: 100rpx;">
		<view class="flex-1 flex align-center justify-center" hover-class="bg-light">
			修改
		</view>
		<view class="flex-1 flex align-center justify-center"hover-class="bg-light"@click="openVideoList">
			视频
		</view>
		<view class="flex-1 flex align-center justify-center"hover-class="bg-light">
			删除
		</view>
		</view>
		<view class="f-divider">
			
		</view>
	</view>
	
</view>
			
</template>

<script>
	 import mediaList from "../../component/common/media-list.vue"
	export default {
		components:{
			mediaList
		},
		data() {
			return {
				list:[{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app实战",
					create_time:"今天六点",
					paly_count:0,
					danmu_count:0
				},
				{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app实战",
					create_time:"今天六点",
					paly_count:0,
					danmu_count:0
				}]
			}
		},
		methods: {
			openVideoList(item){
				uni.navigateTo({
					url:'/pages/user-video-list/user-video-list',
					success: res => {
						
					},
					fail :()=>{
						
					},
					complete:()=>{
						
					}
				})
			}
		}
	}
</script>

<style>

</style>
