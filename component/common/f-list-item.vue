<template>
	<view class="p-3 py-2 flex align-center" hover-class="bg-light" @click="$emit('click')"
	>
		<text v-if="icon" class="iconfont  mr-3":class="icon"></text>
		<view class="mr-auto font-md">
			{{title}}
		</view>
		<view class="text-muted font">
			{{rightText}}	<text  v-if="showRightIcon" class="iconfont iconjinru ml-1 text-light-muted"></text>
		</view>
	
	</view>
</template>

<script>
export default{
	props:{
		icon:{ 
			type:String,
			default:""
			
		},
		title:{
			type:String,
			default:""
		},
		rightText:{
			type:String,
			default:""
		}
		,
		showRightIcon:{
			type:Boolean,
			default:true
		}
	}
}
</script>

<style>
</style>