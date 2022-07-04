<template>
  <h3>我是App组件(祖)</h3>
</template>

<script>
import { ref,reactive,toRefs,readonly,isRef,isProxy,isReadonly,isReactive } from 'vue'
export default {
    name: "App",
	setup(){
		let car= reactive({name:'奔驰',price:'40w'})
		let sum=ref(0)
		let car2=readonly(car)

		console.log(isRef(sum));
		console.log(isReadonly(car2));
		console.log(isProxy(car));
		console.log(isProxy(car2));
		console.log(isProxy(sum));
		console.log(isReactive(car));
		return {...toRefs(car)}
	}
}
</script>

<style>
.app{
	background-color: gray;
	padding: 10px;
}
</style>