<!-- vue3中的watch只能监视以下四中数据 -->
<!-- 1.ref定义的数据 -->
<!-- 2.reactive定义的数据 -->
<!-- 3.函数返回一个值 -->
<!-- 4.一个包含以上内容的数组 -->

<script lang="ts" setup>
defineOptions({
  name: 'Person123',
})

import { reactive, watch } from 'vue'

// 数据
// reactive定义的对象不可整体修改
let person = reactive({
  name: '张三',
  age: 18,
})

let obj = reactive({
  a: {
    b: {
      c: 666,
    },
  },
})
// 方法
function changeName() {
  person.name += '~'
}
function changeAge() {
  person.age += 1
}
function changePerson() {
  // person的地址值没有变化。
  Object.assign(person, { name: '李四', age: 80 })
}

function test() {
  obj.a.b.c = 888
}

// 监视
// 情况三：监视【reactive】定义的【对象类型】数据，且默认是开启深度监视的
watch(person, (newValue, oldValue) => {
  console.log('person变化了', newValue, oldValue)
})

watch(obj, (newValue, oldValue) => {
  console.log('obj变化了', newValue, oldValue)
})
</script>

<template>
  <div class="person">
    <h1>情况三：监视【reactive】定义的【对象类型】数据</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changePerson">all in</button>
    <hr />
    <h2>测试：{{ obj.a.b.c }}</h2>
    <button @click="test">修改obj.a.b.c</button>
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
