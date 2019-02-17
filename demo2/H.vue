<template>
<div class="H">
	<p>H组件内容</p>
	<button ref="btn">安妮</button><!-- ref属性相当于识别标签的记号，相当于class,然后在rhis.$refs属性中选取 -->
	
	<br />
	<!-- ref的循环，一个ref名称选择多个标签，在refs属性里面是一个数组，可以按索引分别选取 -->
	<button ref="btn1" v-for="cen in [1,2,3,4]">{{cen}}</button>
	
	<Props v-on:AA='A' v-bind:a="mg" />
	<p>{{cen}}</p>
	
	<Ref ref="msg" ef='我是ef数据' />
	
	<p> {{nem}}</p>
	
	<button v-on:click="num++">自增加</button>{{num}}
</div>
</template>

<script>
	import Props from "@/components/Props";
	import Ref from "@/components/Ref";
	export default {
		name: 'H',
		components:{Props,Ref},
		data() {
			return {
				cen:"",
				nem:"",
				mg:"我是动态属性",
				n1:"我是H组件的数据n1",
				n2:"我是H组件的数据n2",
				n3:"我是H组件的数据n3",
				num:1
			};
		},
		methods:{
			A(a){
				console.log(a)
				this.cen=a
			}
		},
		mounted(){
		console.log("H组件已挂载")
		this.$refs.msg.givemsg("我是父组件向Ref组件传递的数据")
		this.nem=this.$refs.msg.name	
		console.log(this.$children[1].name)
	   },
	   destroyed() {
	   	console.log("H组件已销毁")
	   }
	}
</script>

<style scoped>

</style>
