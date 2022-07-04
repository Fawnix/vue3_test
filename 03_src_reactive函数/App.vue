<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息:</h1>
  <h2>姓名:{{person.name}}</h2>
  <h2>年龄:{{person.age}}</h2>
  <h2>爱好:{{person.hobby}}</h2>
  <h2>工作种类:{{person.job.type}}</h2>
  <h2>工作薪水:{{person.job.salary}}</h2>
  <h2>测试一下:{{person.job.a.b.c}}</h2>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import {reactive} from 'vue'
export default {
  name: 'App',
  setup(){
    // 数据，ref把一个普普通通的字符串变成一个响应式的数字
/*  let name=ref('张三')
    let age=ref(18)
    let job=reactive({
      type:'前端工程师',
      salary:'30k',
      a:{
        b:{
          c:666
        }
      }
    })
    let hobby= reactive(['抽烟','喝酒']) */

  let person=reactive({
      name:'张三',
      age:18,
      job:{
      type:'前端工程师',
      salary:'30k',
      a:{
        b:{
          c:666
        }
      }
    },
    hobby:['抽烟','喝酒']
  })

    // 方法
    function changeInfo(){
      /* name.value='李四'
      age.value=40
      job.value.type='UI设计师'
      job.value.salary='60k' */

      // .value是为了取ref里面真正传入的数据，ref其实也求助了reactive函数，将数据 变为真正的proxy实例对象
      person.name='李四'
      person.age=40
      person.job.type='UI设计师'
      person.job.salary='60k'
      person.job.a.b.c=999
      person.hobby[0]='学习'
    }

    // 返回一个对象(常用)
    return{
      person,
      changeInfo,
    }
  }
}
</script>

