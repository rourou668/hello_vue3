<script lang="ts" setup>
defineOptions({
  name: 'Person123',
})

import { ref } from 'vue'
//数据
let name = ref('张三') //想让谁有响应式，就在外面包一个ref
let age = ref(18)
let tel = '1388888888'
let address = '北京'

// 方法
function changeName() {
  name.value = 'zhang-san' //与之对应的要改为xxx.value
  console.log(name)
}
function changeAge() {
  age.value += 1
}
function showTel() {
  alert(tel)
}
</script>

<template>
  <div class="person">
    <h2>姓名:{{ name }}</h2>
    <h2>年龄:{{ age }}</h2>
    <h2>地址：{{ address }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="showTel">查看联系方式</button>
  </div>
</template>

<style scoped>
.person {
  background-color: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}
button {
  margin: 0 10px;
}
</style>
