<template>
<div class="E">
	<p>我是E组件</p>
	姓名：<input type="text" v-bind:value="name" /><br />
	<!-- 绑定属性 如果只写value=“name”，只会当成字符串看待，加上bind，就会被识别到是return的数据 -->
	密码：<input type="text" :value="pwd" />
	<!-- ：value是v-bind：value的缩写 -->
	<p v-bind:class="{a:false,b:true}" v-bind:style="{color:red}">可以不直接写布尔值，而通过数据</p>
	<p v-bind:class="[true?'a':'b']">三目运算，需带中括号,数据需要加引号</p>
	<p v-bind:class="[{a:true},'b']">数组class</p>
	<p v-bind:style="Sty">内联样式，绑定一个json对象</p>
	<p v-bind:style="[{color:'orange',fontWeight:'bold'}]">内联样式,数组样式</p>
	<!-- 方法 -->
	<p>{{A()}}</p>
	<!-- 事件 -->
	<button v-on:click="B($event)">ann</button>
	
	<!-- 事件修饰符 -->
	
	<button v-on:click.once="M1($event)">按钮1</button><!-- once表示事件只能执行一次 -->
	<div style="width: 100%;height: 50px;border: 1px solid lavender;margin: 10px 0;" v-on:click="M2()">
			<button v-on:click.stop="M2()">按钮2</button><!-- stop表示阻止事件冒泡 -->
	</div>
	
	<div style="width: 100%;height: 50px;border: 1px solid lavender;margin: 10px 0;" v-on:click.self="M3(1)">
			<!-- self表示触发事件是标签本身的时候才会执行，也能避免冒泡 -->
			<button v-on:click="M3(2)">按钮2</button>
	</div>
	
	<a href="http://www.baidu.com" v-on:click.prevent>百度</a><!-- 阻止默认行为。此处是阻止链接跳转 -->
	
	
	<div v-on:click.capture="M4(1111)" style="width: 100%;height: 50px;border: 1px solid lavender;margin: 10px 0;" >
			<!--capture不加时，就是事件冒泡，也就是点击按钮时，先执行按钮绑定事件，再执行父标签的绑定事件 -->
			<!--加capture时，就是事件捕获，也就是点击按钮时，先执行父标签的绑定事件，再执行按钮绑定事件 -->
			<button v-on:click="M4(2222)">按钮2</button>
	</div>
	
	<!-- 键盘事件 -->
	<input type="text" @keyup.enter="down($event)" value="enter" />
	<input type="text" @keydown="up($event)" value="value" /><!-- keydown比keyup晚一步，不能实时获取 -->
	<br />
	<p>方向键：{{txt}}keycode:{{num}}</p>
	<input type="text" @keyup.up="txt='上',num=down($event)" value="up" />
	<input type="text" @keyup.down="txt='下',num=down($event)" value="down" />	
	<input type="text" @keyup.left="txt='左',num=down($event)" value="left" />
	<input type="text" @keyup.right="txt='右',num=down($event)" value="right" />
	<br />
	<input type="text" @keyup.space="down($event)" value="space" />
	<input type="text" @keyup.esc="down($event)" value="esc" />
	<input type="text" @keyup.delete="down($event)" value="delete" />
	<input type="text" @keyup.esc="down($event)" value="esc" />
	<input type="text" @keyup.r="down($event)" value="r" />
	<input type="text" @keyup.32="down($event)" value="32" />
	<input type="text" @keyup.65="down($event)" value="65" />
	<input type="text" @keydown.alt="down($event)" value="alt" />
	<input type="text" @keydown.shift="down($event)" value="shift" />
	<input type="text" @keydown.ctrl="down($event)" value="ctrl" />
	<input type="text" @keydown.65.68="down($event)" value="ctrl+D" />
</div> 
</template>

<script>
	export default {
		name: 'E',
		data() {
			return {
				name:"admin",
				pwd:"123",
				red:"darkred",
				Sty:{
					color:"#42B983",
					fontWeight:"bold"
				},
				txt:"",
				num:""
			};
		},
		methods:{
			A:function(){
				console.log(this)/* 方法中的this,不管有没有绑定事件，指代的就是整个组件，里面存有所有的数据，方法等 */
				console.log(this.Sty.color)/* 一般来说，正确的书写格式是A:function A(){},但是在Es6中可以缩写：A(){} */
		      	console.log(this.$data)/* 所以可以输出整个data,但是前面需加 $ */
			},/* methods是一个属性，不同于data是一个方法。methods里面存的是json对象 */
			B(e){
				console.log(e)
				console.log(e.target)/* 如果有子元素的话，target有可能是子元素 */
				console.log(e.currentTarget)/* 当前触发事件的标签，不是子元素 */
			},
			M1(e){
				console.log("执行")
			},
			M2(){
				console.log("m2执行")
			},
			M3(n){
				console.log("执行m3   "+n)
			},
			M4(n){
				console.log("执行m4   "+n)
			},
			down(e){
				console.log(e.keyCode);
				return (e.keyCode)
			},
			up(e){
				console.log(e.currentTarget.value)
			}
		}
	}
</script>

<style scoped>
.a{
	color: #42B983;
}
.b{
	font-weight: bold;
}
</style>
