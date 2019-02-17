<template>
<div class="blue">
	
	<!-- 1. v-text 指令用于更新标签包含的文本 -->
    <p v-text="msg"></p>
    <!--效果相同-->
    <p>{{ msg }}</p>

    <!-- 2. v-html 指令绑定一些包含html代码的数据在视图上 -->
    <p v-html="name"></p>

    <!-- 3. v-show 指令控制元素的display css属性 -->
    <p v-show="show_true">因为执行了v-show，且数据为true，所以我的display是可见的</p>
    <p v-show="show_false">数据为false，我的display是不可见的</p>

    <!-- 4. v-if 指令 指令控制元素是否需要被渲染出来 -->
    <p v-if="if_true">因为执行了v-if，且数据为true，所以我被渲染出来了</p>
    <p v-if="if_false">我是false，我没有被渲染出来</p>

    <!-- 5. v-else 指令 前一个兄弟节点必须要使用 v-if 指令 -->
    <p v-if="if_1">我是if，但是数据是false，所以我不能被渲染</p>
    <p v-else>因为我前面的兄弟if的数据是false，而我是else,所以我被渲染出来了</p>

    <p v-if="type == 'A'">A</p>
    <p v-else-if="type =='B'">
		因为只有我的v-else-if的指令的判断是true，所以只有我被渲染出来了，
		而其他的v-if,v-else-if,v-else都没被显示</p>
    <p v-else-if="type == 'C'">C</p>
    <p v-else>Not A/B/C</p>

    <!--6.循环指令-->
    <div v-for="can in [1,2,3,4]">{{can}}</div>
    <div v-for="(can,index) in list">{{index}}.{{can}}</div>
<!--这两个参数，第一个是数组的值，第二个是索引号，参数名称都可以任意切换 -->
    <p v-for="cn in [{msg:'1'}, {msg:'2'}, {msg:'3'}]">{{cn.msg}}</p>
    <p v-for="(v, k,t) in items2"> {{ t}}.{{k}}: {{v}}</p>
<!--数据是个json对象，那么，第一个参数是value值，第二个参数是属性名。最后一个参数是索引-->

    <!--template 本身不会输出，只会重复创建p标签,
	意思就是如果父标签不是template，而是div，那么循环几次就会创建几个div
	如果加上template，那么就只有一个div，里面会有很多p标签
	-->
    <template v-for="item in [1,2,3,4]">
      <span>消息提示:</span>
      <span>{{ item}}</span>
    </template>

    <!-- 7. v-model 指令 这是一个最重要最常用的指令，一般用在表单输入,实现表单控件和数据的双向绑定 -->
    <div>
      <input v-model="msg" type="text"><!-- 使用v-model，msg随着文本框的value值变化 -->
      <p>你输入:{{ msg }}</p>
    </div>
    <!-- 8. v-once 指令特点是只渲染一次，后面元素中的数据再更新变化，都不会重新渲染 -->
    <div>
      <input v-model="msg1" type="text">
      <p v-once>你输入：{{ msg1 }}</p><!-- 使用v-once，msg只会渲染一次，不会更新 -->
      <p>你输入：{{ msg1 }}</p>
    </div>
	
	<!-- v-pre实行不编译 -->
	<p v-pre>{{1+1}}</p>
</div>
</template>

<script>
	export default {
		name: 'B',
		data() {
			return {
		msg:"第一次的msg",
		msg:"我是之后更新过的msg",
        name:"<b>小强</b>",
        show_true:true,
        show_false:false,
        if_true:true,
        if_false:false,
        if_1:false,
        type:"B",
        list:['数据1','数据2','数据3'],
        items2:{title: '标题', value: '内容', age: 30},
        msg1:"hello 你好"

			};
		}
	}
</script>

<style scoped>
.blue{
	color: lightcoral;
	font-size: 14px;
	line-height: 20px;
}
</style>
