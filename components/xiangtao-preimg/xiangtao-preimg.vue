<template>
	<view class="xt-content">
		<view class="xt-main">
			<view class="xt-main-item" v-for="(item, i) in urls" :key="i">
				<image :src="item.url"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			urls: {
				type: Array
			}
		},
		data() {
			return {
				
			};
		},
		onLoad() {
			console.log(JSON.stringify(this.urls))
		}
	}
</script>

<style lang="scss" scoped>
	.xt-content {
		width: 750upx;
		height: 750upx;
		background: black;
		.xt-main {
			width: 100%;
			height: 100%;
			display: flex;
			flex-wrap: nowrap;
			flex-direction: row;
			&-item{
				image {
					width: 750upx;
					height: 100%;
				}
			}
		}
	}
	
</style>
