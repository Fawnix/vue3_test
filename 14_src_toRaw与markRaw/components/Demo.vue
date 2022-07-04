<template>
<h4>当前求和为:{{sum}}</h4>
<button @click="sum++">点我sum++</button>
    <h1>姓名：{{name}}</h1>
    <h1>年龄：{{age}}</h1>
    <h1 v-show="person.car">座驾信息：{{person.car}}</h1>
    <h1>薪资：{{job.j1.salary}}K</h1>
    <button @click="name+='~'">修改姓名</button>
    <button @click="age++">增长年龄</button>
    <button @click="job.j1.salary++">增长薪资</button>
    <button @click="showRawPerson">输出最原始的person</button>
    <button @click="addCar">给人添加一辆车</button>
    <button @click="person.car.name+='!'">换车名</button>
    <button @click="changePrice">换价格</button>
</template>

<script>
import {reactive, toRefs, ref,toRaw, markRaw} from 'vue'
	export default {
		// eslint-disable-next-line vue/multi-word-component-names
		name: 'Demo',
        setup(){
            let sum=ref(0)
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
        
        function showRawPerson(){
            /* const p=toRaw(person)
            p.age++
            console.log(p); */
            
            const sum=toRaw(sum)
        }

        function addCar(){
            let car={name:'奔驰',price:40}
            person.car=markRaw(car)
        }

        function changePrice(){
            person.car.price++
            console.log(person.car.price);
        }

		//返回一个对象（常用）
		return {
            sum,
            person,
            showRawPerson,
            ...toRefs(person),
            addCar,
            changePrice
        }
	}
    }
</script>