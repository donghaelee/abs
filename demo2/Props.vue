<template>
<div>
	<button v-on:click="B()">我是P组件</button>
	{{a}}
	{{$parent.n1}}
	{{$parent.n2}}
	{{$parent.n3}}
</div>
</template>

<script>
	export default {
		name: 'Props',
		props:["a"],
		data() {
			return {
				
			};
		},
		methods:{
			B(){
				this.$emit("AA","我是Props子组件向父组件传递的数据",111)
			}
		},
		created() {
			console.log(this.$parent)
		}
	}
</script>

<style scoped>

</style>
