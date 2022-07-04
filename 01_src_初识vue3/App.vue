<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息:</h1>
  <h2>姓名:{{name}}</h2>
  <h2>年龄:{{age}}</h2>
  <h2>性别:{{sex}}</h2>
  <button @click="sayHello">说话(vue3所配置的——sayHello)</button><br><br>
  <button @click="sayWelcome">说话(vue2所配置的——sayWelcome)</button><br><br>  
  <button @click="test1">测试一下在vue2配置中读取vue3的数据、方法</button><br><br>  
  <button @click="test2">测试一下在vue3配置中读取vue2的数据、方法</button><br><br>  
</template>

<script>
// import {h} from 'vue'
export default {
  name: 'App',
  data(){
    return{
      sex:'男'
    }
  },
  methods:{
    sayWelcome(){
      alert('欢迎来到尚硅谷学习')
    },
    test1(){
      console.log(this.sex);
      console.log(this.name);
      console.log(this.age);
      console.log(this.sayHello);
    }
  },
  // 此处只是测试一下setup，暂时不考虑响应式的问题
  setup(){
    // 数据
    let name='张三'
    let age=18

    // 方法
    // eslint-disable-next-line no-unused-vars
    function sayHello(){
      alert(`你好啊，我叫${name}，我${age}岁了`)
    }
    function test2(){
      console.log(this.sex);
      console.log(this.name);
      console.log(this.age);
      console.log(this.sayWelcome);
    }

    // 返回一个对象(常用)
    return{
      name,
      age,
      sayHello,
      test2
    }

    // 返回一个函数(渲染函数)
    // return ()=>h('h1','尚硅谷')
  }
}
</script>

