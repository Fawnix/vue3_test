<template>
  <div class="child">
	<h3>我是Child组件</h3>
  {{sum}}
  </div>
</template>

<script>
import {ref} from 'vue'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: "Child",
    setup(){
      let sum=ref(0)
      // eslint-disable-next-line no-unused-vars
      return new Promise((resolve,reject)=>{
        setTimeout(()=>{
          resolve({sum})
        },3000)
      })
    }
}
</script>

<style>
.child{
	background-color: blueviolet;
	padding: 10px;
}
</style>