<template>
	<view class="xt-container">
		<view class="mask" v-if="maskShow" @tap="maskTap"></view>
		
		<view id="xt-dialog-main" class="xt-main" :animation="animationData">
			<view class="xt-main-header" v-if="showTitle == 'true'">
				<view @tap="cancelTap">
					<uni-icon type="clear" size="32" color="#4cd964"></uni-icon>
				</view>
				<view><text>{{title}}</text></view>
				<view @tap="confirmTap">
					<uni-icon type="checkbox-filled" size="32" color="#dd524d"></uni-icon>
				</view>
			</view>
			<view class="xt-main-content">
				<slot />
			</view>
			<view class="xt-main-footer" v-if="showFooter == 'true'">
				<view @tap="cancelTap">
					<text>取消</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icon/uni-icon.vue"
	export default {
		components: {uniIcon},
		data() {
			return {
				maskShow: false,
				animationData: {},
				animation: {},
				height: 0
			};
		},
		props: {
			showTitle: {
				type: Boolean,
				default: true
			},
			showFooter: {
				type: Boolean,
				default: false
			},
			title: {
				type: String,
				default: "底部弹框"
			}
		},
		onLoad() {
			this.animation = uni.createAnimation({
				duration: 600,
				timingFunction: 'ease',
			})
		},
		onReady(){
			let view = uni.createSelectorQuery().select(".xt-main");
			var self = this;
			view.boundingClientRect(data => {
				self.height = data.height;
			}).exec();
		},
		methods: {
			confirmTap(){
				this.$emit("confirm", {
					confirm: true,
					cancel: false
				});
				this.hideDialog();
			},
			cancelTap(){
				this.$emit("cancel", {
					confirm: false,
					cancel: true
				});
				this.hideDialog();
			},
			maskTap(){
				this.maskShow = false;
				this.hideDialog();
			},
			showDialog(){
				this.maskShow = true;
				this.animation.translateY(-1 * (this.height + 10)).step()
				this.animationData = this.animation.export();
			},
			hideDialog(){
				this.maskShow = false;
				this.animation.translateY(0).step()
				this.animationData = this.animation.export();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.xt-container {
		width: 96%;
		position: fixed;
		top: 100vh;
		padding: 0 2%;
		
		.mask {
		  position: fixed;
		  top:0;
		  left:0;
		  z-index: 500;
		  width:100%;
		  height:100vh;
		  background: rgba(0, 0, 0, 0.2);
		} 
		
		.xt-main {
			width: 100%;
			position: relative;
			border-radius: 10upx;
			border: 2upx solid #ccc;
			display: flex;
			flex-direction: column;
			z-index: 2000;
			
			&-header{
				width: 100%;
				height: 66upx;
				border-bottom: 1px solid #c1c1c1;
				background: #fff;
				display: flex;
				flex-direction: row;
				flex-wrap: nowrap;
				justify-content: space-between;
				align-items: center;
				view {
					margin: 0 10upx;
					
					text {
						font-size: 24upx;
						line-height: 66upx;
					}
				}
			}
			
			&-content {
				min-height: 200upx;
				max-height: 680upx;
				background: #fff;
				padding: 10upx;
				overflow: hidden;
			}
			
			&-footer {
				width: 100%;
				height: 66upx;
				margin-top: 10upx;
				display: flex;
				
				view {
					width: 100%;
					height: 66upx;
					background: #fff;
					text-align: center;
					line-height: 66upx;
					text{
						font-size: 26upx;
						border-radius: 10upx;
					}
				}
			}
		}
	}
</style>
