<template>
	<view>
         <view v-for="(item,index) in list" :key="index">
	       <!-- <uni-swipe-action >
				<uni-swipe-action-item :options="options" @click="bindClick($event,item)">
					<media-list :item="item" :index="index"></media-list>
				</uni-swipe-action-item>
			</uni-swipe-action> -->
	<uni-swipe-action>
		<uni-swipe-action-item
		
		    :threshold="0"
		    :right-options="options"
		    @click="bindClick($event,item)"
		>
			<media-list :item="item" :index="index"></media-list>
		</uni-swipe-action-item>
			</uni-swipe-action>
</view>


		
	</view>
</template>

<script>
	import mediaList from "../../component/common/media-list.vue"
	import uniSwipeAction from "../../component/uni-ui/uni-swipe-action/uni-swipe-action.vue"
	import uniSwipeActionItem  from "../../component/uni-ui/uni-swipe-action-item/uni-swipe-action-item.vue"
	export default {
		components:{
			mediaList,
			 uniSwipeAction ,
			  uniSwipeActionItem 
		},
		
		data() {
			return {
				options:[{
					text:'取消收藏',
					style: {
						backgroundColor: 'rgb(254,58,49)'
					}
				}],
				list:[
					{ id:1,
						cover:"/static/demo/list2/1.jpg",
						title:"Uni-app实战",
						create_time:"今天六点",
						paly_count:0,
						danmu_count:0
					},
					{
						id:2,
						cover:"/static/demo/list2/1.jpg",
						title:"Uni-app实战",
						create_time:"今天六点",
						paly_count:0,
						danmu_count:0
					}
				]
			}
		},
		methods: {
			bindClick(e,item)
			{
				uni.showToast({
					title:`点击`,
					icon:'none'
				})
			
			}
		}
	}
</script>

<style>

</style>
