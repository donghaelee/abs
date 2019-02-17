<template>
<div>
	<p>我是Ref组件</p>
	{{$attrs.ef}}
	{{title}}
	{{data1}}
</div>
</template>

<script>
	export default {
		name: 'Ref',
		inject:["data1"],
		data() {
			return {
				name:"我是你",
				title:""
			};
		},
		methods:{
			givemsg(m){
				this.title=m
			}
		}
	}
</script>

<style scoped>

</style>
