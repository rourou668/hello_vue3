<script lang="ts" setup>
import { reactive, toRefs, toRef } from 'vue'

defineOptions({
  name: 'Person123',
})

//数据
let person = reactive({
  name: '张三',
  age: 18,
})

//解构赋值
// let { name, age } = person
//相当于把person.name赋值给name,创建了一个新变量。此时，person.name是响应式数据

let { name, age } = toRefs(person)
//此时，name、age为响应式数据
console.log(name)
console.log(age)

let nl = toRef(person, 'age')
console.log(nl.value)

//方法
function changeName() {
  name.value += '~'
  // console.log(name, person.name)
}
function changeAge() {
  age.value += 1
}
</script>

<template>
  <div class="person">
    <h2>{{ person.name }}</h2>
    <h2>{{ person.age }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
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
li {
  font-size: 20px;
}
</style>
