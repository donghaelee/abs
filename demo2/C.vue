<template>
<div class="white">
	<p v-text="data1"></p>
	<p v-html="'<em>小花</em>'"></p>
	<p v-if="true">v-if</p>
	<div>
		<p v-if="false"></p>
		<p v-else>v-else</p>
	</div>
		<div>
		<p v-if="false"></p>
		<p v-else-if="true">v-else-if</p>
		<p v-else>v-else</p>
	</div>
	<p v-show="true">v-show</p>
	<p v-show="false"></p>
	<p v-for="(cen,index) in [1,2,3,4]">{{index}}.{{cen}}</p>
	<p v-for="(a,b,c) in {name:'Carol',sex:'女',age:20}">{{c}}:{{b}}.{{a}}</p>
</div>
</template>

<script>
	export default {
		name: 'C',
		data() {
			return {
				true:true,
				false:false,
				data1:"data1",
				data1:"data1-2"
			};
		}
	}
</script>

<style scoped>
.white{
	line-height: 30px;
	color: black;
	font-size: 18px;
}
</style>
