<template>
    <h4>{{person}}</h4>
    <h1>姓名：{{name}}</h1>
    <h1>年龄：{{age}}</h1>
    <h1>薪资：{{job.j1.salary}}K</h1>
    <button @click="name+='~'">修改姓名</button>
    <button @click="age++">增长年龄</button>
    <button @click="job.j1.salary++">增长薪资</button>
</template>

<script>
import {reactive,toRefs} from 'vue'
	export default {
		// eslint-disable-next-line vue/multi-word-component-names
		name: 'Demo',
        setup(){
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

		//返回一个对象（常用）
		return {
            person,
            ...toRefs(person)
        }
	}
    }
</script>