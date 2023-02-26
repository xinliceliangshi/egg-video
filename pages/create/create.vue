<template>
	<view>
		<view class="bg-light position-relative" style="height: 350rpx;" hover-class="bg-light"
		@tap="upload">
		<image :src="form.cover" mode="aspectFill" style="width: 750rpx;height: 350rpx;">
			<view class="position-absolute left-0 right-0 bottom-0 top-0 flex 
			flex-column align-center
			justify-center" style="background-color: rgba(255, 255, 255, 0.3);">
			<text v-if="!form.cover" class="iconfont iconjia" style="font-size: 50rpx;"></text>
			<!-- <text class="iconfont iconjia" style="font-size: 50rpx;"></text>	 -->
			<!-- <text class="font text-muted">点击添加封面图</text> -->
			<text class="font text-muted">点击 {{form.cover ? '添加':''}}封面图</text>
			</view>
		</view>
		<form-item label="标题">
			<input type="text" v-model="form.title" placeholder="请填写视频标题" placeholder-class="text-light-muted" 
			class="w-100 pr-5"/>
		</form-item>
		<picker mode="selector" :range="range" @change="change">
			<form-item label="分类" rightIcon>
				<input type="text" v-model="form.category" placeholder="请填写视频标题" placeholder-class="text-light-muted" 
				class=" w-100 pr-5" disabled/>
			</form-item>
		</picker>
		
		<form-item label="描述">
			<view class="w-100 pr-5">
		<textarea v-model="form.desc" placeholder="请填写视频描述" style="width: 550rpx;" class="py-3" ></textarea>
			</view>
			
		</form-item>
		<!-- #ifdef MP -->
		<view class="px-2 py-3">
			<main-big-button @tap="submit">发布</main-big-button>
		</view>
		<!-- #endif -->
	
		
	</view>
</template>

<script>
	import formItem from "@/component/common/form-item.vue";
	import mainBigButton from "@/component/common/main-big-button.vue"
	export default {
		components:{
			formItem,
			mainBigButton
		},
		data() {
			return {
				form:{
					cover:"",
					title:"",
					category:"",
					desc:""
				},
				range:["分类1","分类2","分类3"]
			}
		},
		methods: {
			upload()
			{
				uni.chooseImage({
					count:1,
			        sizeType:['compressed'],
					sourceType:['album'],
					success:(res)=>{
					this.form.cover=	res.tempFilePaths[0]
					}
				})
			},
			change(e)
			{
				this.form.category = this.range[e.detail.value];
			},
			submit()
			{}
			
		}
	}
</script>

<style>

</style>
