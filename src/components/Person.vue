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
let person = reactive({
  name: '张三',
  age: 18,
  car: {
    c1: '奔驰',
    c2: '宝马',
  },
})

// 方法
function changeName() {
  person.name += '~'
}
function changeAge() {
  person.age += 1
}
function changeC1() {
  person.car.c1 = '奥迪'
}
function changeC2() {
  person.car.c2 = '大众'
}
function changeCar() {
  person.car = { c1: '雅迪', c2: '爱玛' }
}

// 监视
// getter函数：能返回一个值的函数
// watch(
//   // 若该属性不是对象类型，需要写成函数形式
//   () => person.name,
//   (newValue, oldValue) => {
//     console.log('person.name变化了', newValue, oldValue)
//   },
// )

// 若该属性是对象类型，可直接编，也可写成函数式，建议写成函数式
// watch(person.car, (newValue, oldValue) => {
//   console.log('person.car变化了', newValue, oldValue)
// })

// 此时监视的是对象的地址值
watch(
  () => person.car,
  (newValue, oldValue) => {
    console.log('person.car变化了', newValue, oldValue)
  },
  // 关注对象的内部，需要手动开启深度监视
  {
    deep: true,
  },
)
</script>

<template>
  <div class="person">
    <h1>情况四：监视【ref】或【reactive】定义的【对象类型】数据中的某个属性</h1>
    <h2>姓名:{{ person.name }}</h2>
    <h2>年龄:{{ person.age }}</h2>
    <h2>汽车:{{ person.car.c1 }}、{{ person.car.c2 }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changeC1">修改第一台车</button>
    <button @click="changeC2">修改第二台车</button>
    <button @click="changeCar">修改第整个车</button>
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
