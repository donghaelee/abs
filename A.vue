<template>
	<div class="red">
		我是组件a 
		<C/>
		<D/>
	</div>
</template>

<script>
	import C from "@/components/C"
	import D from "@/components/D"
	export default {
		name: 'A',
		components:{C,D},
		data() {
			return {
				
			};
		}
	}
</script>

<style scoped>
.red{
	color:blue;
	font-size: 30px;
	line-height: 60px;
}
</style>
