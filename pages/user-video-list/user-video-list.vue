<template>
	<view class="bg-light" style="min-height: 100vh;">
			<block v-for="(item,index) in list" :key="index">
				<view v-if="!item.isedit" class="bg-white">
					<video style="height: 350rpx;width: 100%;" :src="item.video" controls></video>
					<form-item label="标题">
						<text class="font">{{item.title}}</text>
					</form-item>
					<view class="flex" style="height: 100rpx;">
						<view class="flex-1 font flex align-center justify-center" hover-class="bg-light" @click="openEdit(item)">修改</view>
						<view class="flex-1 font flex align-center justify-center" hover-class="bg-light" @click="deleteItem(item)">删除</view>
					</view>
				</view>
				<view v-else class="bg-white">
					<view style="height: 350rpx;" class="bg-light position-relative" hover-class="bg-hover-light" >
						<video v-if="item.video" style="height: 350rpx;width: 100%;" :src="item.video" controls></video>
						<view v-if="!item.video" class="position-absolute left-0 right-0 top-0 bottom-0 flex flex-column align-center justify-center" style="background-color: rgba(255,255,255,0.2);"
						@tap="upload(item)">
							<text class="iconfont iconjia" style="font-size: 50rpx;"></text>
							<text class="font text-muted">点击添加视频</text>
						</view>
					</view>
					<view v-if="item.video" class="flex align-center justify-center font border-bottom border-top" hover-class="bg-light" style="height: 100rpx;">
						点击切换视频
					</view>
					<form-item label="标题">
						<input type="text" v-model="item.title" placeholder="请填写视频标题" placeholder-class="text-light-muted" class="w-100 pr-5"/>
					</form-item>
					<form-item label="描述">
						<textarea v-model="item.desc" placeholder="请填写视频描述" style="width: 550rpx;" class="py-3"/>
					</form-item>
					<view class="flex" style="height: 100rpx;">
						<view class="flex-1 font flex align-center justify-center bg-main text-white" hover-class="bg-main-hover" @click="submit(item)">完成</view>
						<view class="flex-1 font flex align-center justify-center" hover-class="bg-light" @click="deletItem(index)">删除</view>
					</view>
				</view>
				<view class="f-divider"></view>
			</block>
			
			
			
			
			
			<view v-if="showButton" class="flex align-center justify-center bg-main text-white font" style="height: 100rpx;" hover-class="bg-main-hover" @click="add">
				+ 添加新章节
			</view>
		</view>
</template>

<script>
	import formItem from '@/component/common/form-item.vue';
	export default {
			components: {
					formItem
				},
		data() {
			return {
				list:[{
					video:"",
					title:"第一节",
					desc:"",
					isedit:false
				}]

				
			}
		},
		computed: {
					showButton() {
						let arr = this.list.filter(item=>{
							return item.isedit
						})
						return arr.length === 0
					}
				},
		methods: {
			submit(item)
			{
				if(!item.video){
									return uni.showToast({
										title: '视频不能为空',
										icon: 'none'
									});
								}
				if(!item.title){
									return uni.showToast({
										title: '标题不能为空',
										icon: 'none'
									});
				}
				item.isedit = false;
			},
			deleteItem(index)
			{
				uni.showModal({
					content: '是否要删除该视频？',
					success: (res)=>{
				this.list. splice(index,1)
				},
				})
			},
			add()
			{
				this.list.push({
					video:"",
					title:"",
					desc:"",
					isedit:true
				})
			},
			upload(item)
			{
				uni.chooseVideo({
					count: 1,
										sourceType: ['camera', 'album'],
										success: (res)=> {
											item.video =res.tempFilePath
											}
				})
			},
			openEdit(item){
				item.isedit=true
			}
		}
	}
</script>

<style>

</style>
