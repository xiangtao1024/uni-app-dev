<template>
	<view class="uni-padding-wrap uni-common-pb">
		<view class="uni-hello-text uni-common-pb">
			组件开发示例
		</view>
		<view class="uni-card" v-for="(list,index) in lists" :key="index">
			<view class="uni-list">
				<view class="uni-list-cell uni-collapse">
					<view class="uni-list-cell-navigate uni-navigate-bottom" hover-class="uni-list-cell-hover"
					 @click="openPage(list)">
						{{list.name}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				lists: [{
						name: '底部对话框',
						path: "/pages/index/bottom-dialog"
					},{
						name: '图片预览',
						path: "/pages/index/preimg"
					}
				]
			}
		},
		onLoad() {
			
		},
		methods: {
			openPage(e) {
				uni.navigateTo({
					url: e.path
				})
			}
		}
	}
</script>

<style>
	page {
		height: auto;
		min-height: 100%;
	}

	.uni-card {
		box-shadow: none;
	}

	.uni-list:after {
		height: 0;
	}

	.uni-list:before {
		height: 0;
	}
</style>