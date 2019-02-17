<template>
	<div>
		我是F组件
		<input type="text" v-model="message" />
		<button v-on:click="A()">销毁</button>
	</div>
</template>

<script>
	export default {
		name: 'F',
		data() {
			return {
				message: "小强"
			};
		},
		methods:{
			A(){
				this.$destroy()
			}
		},
		/* 组件创建 */
		beforeCreate(){
		 //beforeCreate:刚刚new Vue()之后，这个时候，数据还没有挂载呢，只是一个空壳
		  alert('beforeCreate 创建前状态===============');
		},
		created() {
		 //这个时候已经可以使用到数据，也可以更改数据,在这里更改数据不会触发updated函数
		  alert('created 创建完毕状态===============');
		},
		/* 渲染的过程 */
		beforeMount() {
		 //虚拟dom已经创建完成，马上就要渲染,在这里也可以更改数据，不会触发updated
		  alert('beforeMount 挂载前状态===============');
		},
		mounted() {
		  //组件已经出现在页面中，数据、真实dom都已经处理好了,事件都已经挂载好了
		  alert('mounted 挂载结束状态===============');
		},
		/* 数据更新过程 */
		beforeUpdate() {
		  alert('beforeUpdate 更新前状态===============');
		},
		updated() {
		  alert('updated 更新完成状态===============');
		},
		/* 页面销毁 */
		beforeDestroy() {
		  //实例销毁之前调用。在这一步，实例仍然完全可用
		  alert('beforeDestroy 销毁前状态===============');
		},
		destroyed() {
		  //组件的数据绑定、监听...都去掉了,只剩下dom空壳
		  alert('destroyed 销毁完成状态===============');
		}
												   
	}
</script>

<style scoped>

</style>
