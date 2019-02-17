<template>
<div>
	<p>C组件</p>
	{{$route.params.id}}
	{{$route.params.bb}}
</div>
</template>

<script>
	export default {
		name: 'New',
		 beforeRouteEnter (to, from, next) {
			 //在进入路由之前调用
          // 在渲染该组件的对应路由被 confirm 前调用
          // 不！能！获取组件实例 `this`
          // 因为当守卫执行前，组件实例还没被创建
          console.log(to)//to即将要进入的目标
          console.log(from)//from当前导航正要离开的路由
          /*next()//直接进to 所指路由  next: Function: 一定要调用该方法来 resolve 这个钩子。执行效果依赖 next 方法的调用参数。
           next(false) //中断当前路由
           next('route') //跳转指定路由*/
         // next("/cc")
		 /* 通过next的调用 来显示是否能进入某些页面 或者不能进入某些页面,可以通过name或者正则来判断*/
		/* if(to.fullPath.search(/\/C\/d\/d/!=-1)){
			 alert("无权限")
		 }else{
			  next()
		 } */
		 console.log("进入C路由")
         if(to.name=="11"){
         			 alert("无权限")
         }else{
         			  next()
         }
        },
        beforeRouteUpdate (to, from, next) {
			//已经进入组件，当路由发生数据更新时，调用
          // 在当前路由改变，但是该组件被复用时调用
          // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
          // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
          // 可以访问组件实例 `this`
		  console.log("路由发生改变")
          next();
        },
        //这个离开守卫通常用来禁止用户在还未保存修改前突然离开。该导航可以通过 next(false) 来取消。
        beforeRouteLeave (to, from, next) {
		//离开路由之前
          // 导航离开该组件的对应路由时调用
          // 可以访问组件实例 `this`
		  console.log("离开了C路由")
          next();
        }

	}
</script>

<style scoped>

</style>
