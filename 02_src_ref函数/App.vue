<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息:</h1>
  <h2>姓名:{{name}}</h2>
  <h2>年龄:{{age}}</h2>
  <h2>工作种类:{{job.type}}</h2>
  <h2>工作薪水:{{job.salary}}</h2>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import {ref} from 'vue'
export default {
  name: 'App',
  setup(){
    // 数据，ref把一个普普通通的字符串变成一个响应式的数字
    let name=ref('张三')
    let age=ref(18)
    let job=ref({
      type:'前端工程师',
      salary:'30k'
    })

    // 方法
    function changeInfo(){
      name.value='李四'
      age.value=40
      job.value.type='UI设计师'
      job.value.salary='60k'
    }

    // 返回一个对象(常用)
    return{
      name,
      age,
      changeInfo,
      job
    }
  }
}
</script>

