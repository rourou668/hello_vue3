<script lang="ts" setup>
defineOptions({
  name: 'Person123', //组件名
})

import { reactive } from 'vue'
//数据
let car = reactive({ brand: '奔驰', price: 100 })
//普通对象想变成响应式对象，用reactive包裹，成为Proxy函数
// console.log(car)
// console.log(Proxy)

let games = reactive([
  { id: 'afafcq4t01', name: '王者荣耀' },
  { id: 'afafcq4t01', name: '原神' },
  { id: 'afafcq4t01', name: '三国志' },
])

let obj = reactive({
  a: {
    b: {
      c: 666,
    },
  },
})
//方法
function changePrice() {
  car.price += 10
  console.log(car.price)
}

function changeFirstGame() {
  games[0]!.name = '流星蝴蝶剑'
}

function changeObj() {
  obj.a.b.c = 999
}
</script>

<template>
  <div class="person">
    <h2>汽车信息：一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
    <button @click="changePrice">修改汽车的价格</button>
    <br />
    <h2>游戏列表：</h2>
    <ul>
      <li v-for="g in games" :key="g.id">{{ g.name }}</li>
      <!--      item  数据源  遍历的时候每一个节点的唯一标识-->
      <!-- for循环 -->
    </ul>
    <button @click="changeFirstGame">修改游戏名字</button>
    <hr />
    <h2>测试：{{ obj.a.b.c }}</h2>
    <button @click="changeObj">修改数据</button>
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
