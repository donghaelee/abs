<template>
<div>
	<p>Fil组件内容</p>
	<p>{{12.3342|Int()}}</p>
	<p>{{'2019/01/09'|Times()}}</p>
	<p>{{sum}}</p>
	<input type="text" v-model="num" />{{num}}
</div>
</template>

<script>
	export default {
		name: 'Fil',
		inject:['data1'],
		filters:{
			/* v是用来接收需要过滤的数据 */
			Int(v){
				return parseInt(v)
			},
			Times(v){
				return v.replace(/\//g,"-")
			}
		},
		computed:{/* 计算属性，是vue提供处理复杂逻辑的属性 让开发者把复杂的逻辑计算避免写在模板中，这样方便维护 */
			sum(){
				return this.num+this.num2
			}
		},
		watch:{/* 监听数据更新 */
			num(v,oldv){
				console.log("数据更新",v,oldv)
			}
		},
		data() {
			return {
				num:1,
				num2:2
			};
		}
	}
</script>

<style scoped>

</style>
