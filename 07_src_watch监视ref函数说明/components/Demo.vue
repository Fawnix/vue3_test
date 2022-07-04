<template>
	<h1>当前求和为：{{sum}}</h1>
    <button @click="sum++">点我+1</button>
    <hr>
    <h2>当前的信息为：{{msg}}</h2>
    <button @click="msg+='!'">修改信息</button>
    <hr>
    <h1>姓名：{{person.name}}</h1>
    <h1>年龄：{{person.age}}</h1>
    <h1>薪资：{{person.job.j1.salary}}K</h1>
    <button @click="person.name+='~'">修改姓名</button>
    <button @click="person.age++">增长年龄</button>
    <button @click="person.job.j1.salary++">增长薪资</button>
</template>

<script>
import {reactive, ref,watch} from 'vue'
	export default {
		// eslint-disable-next-line vue/multi-word-component-names
		name: 'Demo',
        setup(){
            let sum = ref(0)
            let msg=ref('你好啊')
            let person=reactive({
                name:'张三',
                age:18,
                // 用reactive无论嵌套层次有多深都可以检测到、默认开启了深度监视，而vue2的话就要开启深度监视了
                job:{
                    j1:{
                        salary:20
                    }
                }
            })

        // 情况一：监视ref所定义的一个响应式数据
        /* watch(sum,(newvalue,oldvalue)=>{//如果sum是一个对象就要用sum.value,因为sum是一个基本类型的值所以不用.value
            console.log('sum的值变化了',newvalue,oldvalue);
        },{immediate:true}) */

        // 情况二：监视ref所定义的多个响应式数据
        /* watch([sum,msg],(newvalue,oldvalue)=>{
            console.log('sum或msg的值变化了',newvalue,oldvalue);
        },{immediate:true}) */

        /* 情况三：监视reactive所定义的一个响应式数据的全部属性
            1.此处无法正常获取oldvalue
            2.强制开启了深度监视(deep配置无效) */
        /* watch(person,(newvalue,oldvalue)=>{
            console.log('sum的值变化了',newvalue,oldvalue);
        },{immediate:true}) */
       /*  watch(person,(newvalue,oldvalue)=>{
            console.log('sum的值变化了',newvalue,oldvalue);
        },{deep:false}) *///此处的deep配置无效

        // 情况四：监视reactive所定义的一个响应式数据的某个属性
        /* watch(()=>person.name,(newvalue,oldvalue)=>{
            console.log('person的name值变化了',newvalue,oldvalue)
        }) */

         // 情况五：监视reactive所定义的一个响应式数据的某些属性
        watch([()=>person.name,()=>person.age],(newvalue,oldvalue)=>{
            console.log('person的name值或age变化了',newvalue,oldvalue)
        })

		//返回一个对象（常用）
		return {
			sum,
            msg,
            person
        }
	}
    }
</script>