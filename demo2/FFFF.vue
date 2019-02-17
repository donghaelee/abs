<template>
  <div id="app">
	  <div>
	  <button v-for="(t,index) in [1,2,3]" @click="S(index)">{{index}}</button>
	  </div>
	<!--  
	 <div class="box" v-if="no[0]">选项1</div>
	  <div class="box" v-if="no[1]">选项2</div>
	  <div class="box" v-if="no[2]">选项3</div> -->
	 
	  <div class="box" v-if="yes[0]">选项1</div>
	  <div class="box" v-if="yes[1]">选项2</div>
	  <div class="box" v-if="yes[2]">选项3</div>
	  
	  {{data1}}
	  {{yes}}
  </div>
</template>

<script>
export default {
    name: 'App' ,/* 导出一个名为App的组件*/
	data(){
		return{
		     no:[true,false,false],
			 yes:[true,false,false],
			 data1:"1111"
		}
	},
	methods:{
		S(e){
			var di=document.querySelectorAll(".box");
			var btn=document.querySelectorAll("button");
			for(var i=0;i<this.no.length;i++){
				btn[i].style.background="lightblue"
			/* 	this.no.splice(i,1,false) */
				this.yes[i]=false
			}
			btn[e].style.background="red"
		/* 	this.no.splice(e,1,true) */
			this.data1=e
			this.yes[e]=true
		}
	},
	watch:{
		yes:{
			handler:function(){
				console.log("改变")
			},
			deep:true
		}

	}
}
</script>

<style>
*{
	padding: 0;
	margin: 0;
	}
input{
		outline: none;
		width: 300px;
		height: 30px;
		line-height: 30px;
		padding-left: 10px;
		margin: 10px 0;
	}	
p{
		line-height: 30px;
	}
button{
	border: 1px solid black;
	line-height: 30px;
	height: 30px;
	background: lightblue;
	padding: 0 20px;
	outline: none;
	margin: 5px;
}	
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
 font-size: 14px;
	padding: 20px;
}
.box{
	width: 400px;
	height: 200px;
	background: lightblue;
	color: white;
	font-size: 60px;
	text-align: center;
	line-height: 200px;
	float: left;
}
.fade-enter{
	height: 0;
}
.fade-enter-active{
	transition:height 2s;
}
.fade-enter-to{
	height: 200px;
}
.fade-leave{
	height: 200px;
}
.fade-leave-active{
	transition:height 2s;
}
.fade-leave-to{
	height:0;
}
#app button:first-of-type{
	background: red;
}
</style>/* 组件的样式*/

