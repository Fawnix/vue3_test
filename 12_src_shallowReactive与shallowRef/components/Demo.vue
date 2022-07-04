<template>
<h4>当前的x、y值是:{{x.y}}</h4>
<button @click="x={y:888}">点我替换x</button>
<button @click="x.y++">点我x.y++</button>
    <h4>{{person}}</h4>
    <h1>姓名：{{name}}</h1>
    <h1>年龄：{{age}}</h1>
    <h1>薪资：{{job.j1.salary}}K</h1>
    <button @click="name+='~'">修改姓名</button>
    <button @click="age++">增长年龄</button>
    <button @click="job.j1.salary++">增长薪资</button>
</template>

<script>
import {reactive, toRefs, shallowRef} from 'vue'
	export default {
		// eslint-disable-next-line vue/multi-word-component-names
		name: 'Demo',
        setup(){
            // let person=shallowReactive({//只考虑第一层数据的响应式
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
            let x=shallowRef({
                y:0
            })

		//返回一个对象（常用）
		return {
            x,
            person,
            ...toRefs(person)
        }
	}
    }
</script>