<template>
<div class="Slot">
	<p>Slot组件内容</p>
	<slot name="A" a="数据1" b="数据2"></slot>
</div>
</template>

<script>
	export default {
		name: 'Slot',
		data() {
			return {
				
			};
		},
		mounted() {
			console.log(this)
		}
	}
</script>

<style scoped>

</style>
