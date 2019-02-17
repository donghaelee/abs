<template>
<div class="D">
	喜欢的学科：<br/>
	语文：<input type="checkbox" v-model="num" value="语文"/>
	数学：<input type="checkbox" v-model="num" value="数学"/>	
	英语：<input type="checkbox" v-model="num" value="英语"/>
	体育：<input type="checkbox" v-model="num" value="体育"/>
	<br/>
	您已选择:{{num}}<br/>
	性别：<br/>
	<input type="radio" v-model="sex" value="男" />
	<input type="radio" v-model="sex" value="女" />
	<br/>
	您已选择：{{sex}}
	<br/>
	性取向：<br/>
	<select v-model="sEx">
		<option>请选择你的性取向</option>
		<option value="男">男</option>
		<option value="女">女</option>
		<option value="无性别">无性别</option>
		<option value="双性恋">双性恋</option>
	</select>
	<br/>
	您已选择：{{sEx}}
	<br/>
	<input type="text" v-model.lazy="txt" />{{txt}} <!-- 加上lazy之后就是失去焦点时改变后面的txt-->
	<input type="number" v-model.number="Num" />{{Num+1}} <!-- 加上number之后就是数字相加而不是字符串相加-->
	<input type="text" v-model.trim="tXt" />{{tXt}} <!-- 删除前后空格-->
	
</div>
</template>

<script>
	export default {
		name: 'D',
		data() {
			return {
				num:[],
				sex:"男",
				sEx:"",
				txt:"123",
				Num:0,
				tXt:""
			};
		}
	}
</script>

<style scoped>
input{
	margin-right: 20px;
}
</style>
