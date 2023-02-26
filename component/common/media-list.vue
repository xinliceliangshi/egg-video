<template>
	<view  class="flex align-center py-2 border-bottom" style="width: 100%;">
		<image :src="item.cover" style="width: 260rpx; height :160rpx"
		class="rounded-lg mx-2 flex-shrink"
		></image>
		<view class="flex-1 flex-column flex">
			<text class="font" style="line-height: 1.2;">{{item.title}}</text>
			<text class="font-sm text-light-muted mt-auto">{{item.create_time}}</text>
			<view class="flex align-center justify-between text-light-muted line-h">
				<view class="line-h">
					<text class="iconfont iconbofangshu mx-1 font-md"></text>
					<text class="font-sm">{{item.paly_count}}</text>
				</view>
				<view class="line-h">
					<text class="ml-auto iconfont icondanmushu font-md mx-1"></text>
					<text class="font-sm">{{item.danmu_count}}</text>
						
				</view>
			<text class="iconfont icongengduo ml-auto"></text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	props:{
		item:Object,
		index:[String,Number],
		
		
		
	},
	
}
</script>

<style>
</style>