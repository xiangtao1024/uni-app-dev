<template>
	<view>
		<button @tap="showAndHide()">点击</button>
		<xiangtao-dialog ref="xiangtaoDialog" @confirm="confirm" @cancel="cancel" showTitle="true" showFooter="true">
			<view>
				<button>操作1</button>
				<button style="margin-top: 10upx">操作1</button>
				<button style="margin-top: 10upx">操作1</button>
				<button style="margin-top: 10upx">操作1</button>
				<picker-view indicator-style="height: 80px" value="[9999, month - 1, day - 1]">
					<picker-view-column>
						<view class="item" v-for="(item,index) in 10" :key="index">{{item}}年</view>
					</picker-view-column>
					<picker-view-column>
						<view class="item" v-for="(item,index) in 12" :key="index">{{item}}月</view>
					</picker-view-column>
					<picker-view-column>
						<view class="item" v-for="(item,index) in 30" :key="index">{{item}}日</view>
					</picker-view-column>
				</picker-view>
			</view>
		</xiangtao-dialog>
	</view>
</template>

<script>
	import xiangtaoDialog from "@/components/xiangtao-dialog/xiangtao-dialog.vue"
	export default {
		components: {xiangtaoDialog},
		data() {
			return {
				show: false
			};
		},
		methods: {
			confirm(e){
				console.log(JSON.stringify(e));
			},
			cancel(e){
				console.log(JSON.stringify(e));
			},
			showAndHide(){
				this.show = !this.show;
				this.$refs.xiangtaoDialog.showDialog();
			}
		}
	}
</script>

<style lang="scss">

</style>

