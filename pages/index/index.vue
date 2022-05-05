<template>
	<view>
		<view>
			<view style="padding: 50rpx;background-color: green;">
				标头
			</view>
			
			<view style="display: flex;align-items: center;">
				<view style="flex:2">左边</view>
				<scroll-view style="height:100vh;flex:8" scroll-y="true" refresher-enabled="true" :refresher-triggered="triggered"
					:refresher-threshold="100" refresher-background="lightgreen" @refresherrefresh="onRefresh" :lower-threshold="50"
					@scrolltolower="addList"
					@refresherrestore="onRestore" @refresherabort="onAbort">
					
					<view v-for="item,index in list" :key="index" style="padding:40rpx 20rpx;border-bottom: 1rpx solid #ccc;">
						{{item}}
					</view>
				</scroll-view>
			</view>
		</view>
	
	</view>
</template>


<script>
	export default {
		data() {
			return {
				triggered: 'restore',
				list:['giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao']
			}
		},
		onLoad() {},
		methods: {
			onRefresh() {
				console.log("刷新开始")
				setTimeout(() => {
					this.list = ['giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao']
					this.triggered = false;
				}, 1000)
			},
			onRestore() {
				this.triggered = 'restore'; // 需要重置
				console.log("触发刷新");
			},
			onAbort() {
				console.log("被终止事件");
			},
			addList(){
				console.log("我被拉倒底部了")
				
				let list = ['giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao','giao']
				
				this.list = this.list.concat(list)
			}
		}
	}
</script>

<style>
</style>
