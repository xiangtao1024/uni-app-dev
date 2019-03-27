<template>
	<view>
		<button @tap="showAndHide()">点击</button>
		
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

