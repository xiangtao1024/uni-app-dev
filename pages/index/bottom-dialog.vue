<template>
	<view>
		<!-- <button @tap="showAndHide1()">一般用法</button> -->
		<button @tap="showAndHide2()">ActionSheet</button>
		<!-- <xiangtao-dialog ref="xiangtaoDialog1" title="一般用法" @confirm="confirm" @cancel="cancel" showTitle="true" showFooter="true"></xiangtao-dialog> -->
		
		<xt-bottom-dialog ref="xiangtaoDialog2" title="ActionSheet" @confirm="confirm" @cancel="cancel" showTitle="false" showFooter="false">
			<button>操作1</button><button>操作2</button><button>操作3</button>
			<button>操作4</button><button>操作5</button><button>操作6</button>
			<button>操作7</button><button>操作8</button><button>操作9</button>
		</xt-bottom-dialog>
	</view>
</template>

<script>
	import xtBottomDialog from "@/components/xt-dialog/xt-bottom-dialog.vue"
	export default {
		components: {xtBottomDialog},
		data() {
			return {
				
			};
		},
		methods: {
			confirm(e){
				console.log(JSON.stringify(e));
			},
			cancel(e){
				console.log(JSON.stringify(e));
			},
			showAndHide1(){
				this.$refs.xiangtaoDialog1.showDialog();
			},
			showAndHide2(){
				this.$refs.xiangtaoDialog2.showDialog();
			}
		}
	}
</script>

<style lang="scss">

</style>

