<template>
	<view>
		<card title="热门分类" :showRefresh="false">
			<scroll-view scroll-x="true" class="scroll-row">
				<icon-cate v-for="(item,index) in list":key="index" :item ="item"
				:index="index"></icon-cate>
			</scroll-view>
			<view class="f-divider">
				
			</view>
			<card title="全部分类" :showRefresh="false">
				<icon-cate v-for="(item,index) in list":key="index" :item="item":index="index"></icon-cate>
			</card>
		</card>
	</view>
</template>

<script>
	import card from "@/component/common/card.vue"
	import iconCate from "@/component/common/icon-cate.vue"
	export default {
		components:{
		card	,
		iconCate
		},
		data() {
			return {
			list:[
				
			]	
			}
		},
		onLoad() {
			for (let i=0;i<10;i++) {
				this.list.push({
					name:"分类",
					cover:"/static/demo/cate/1%20(1).png"
				})
			}
		
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
