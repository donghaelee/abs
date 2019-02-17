<template>
<div>
	<p>User组件内容</p>
	<button @click="zhen=true">展示</button>
	<button @click="zhen=false">删除</button>
	<button v-aaa="'green'" v-if="zhen">{{num}}</button>
	<input type="text" v-model="num" />
</div>
</template>

<script>
	export default {
		name: 'User-Defined',
		data(){
			return{
				zhen:true,
				num:1
			}
		},
		directives:{
			aaa:{
				bind(el,se){//只调用一次，指定第一次绑定在标签上 完成后调用，参数el是固定的，是指令所包含的绑定的标签
					console.log(el)
					console.log(se)//输出的是一个对象，参数是对象中的value
				},
				inserted(el,se){//被绑定指令的标签 插入到父元素中调用
					el.style.background=se.value
					console.log(se.value)
				},
				update(el){//指令里面或者指令包含的标签 数据发生改变的时候执行 此时dom还没更新
					console.log("update:"+el.innerText)
				},
				componentUpdated(el){//当前组件或绑定指定的标签 数据及dom更新完以后执行,
				//所以前面的update更新永远比componentUpdated模板更新慢一步
					console.log("componentUpdate:"+el.innerText)
				},
				unbind(el){
					console.log("指定解绑")
				}
			}
		},
		}
</script>

<style scoped>

</style>
