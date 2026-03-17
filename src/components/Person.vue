<script lang="ts" setup>
defineOptions({
  name: 'Person123', //组件名
})

import { reactive, ref } from 'vue'
//数据
let car = ref({ brand: '奔驰', price: 100 })

let games = ref([
  { id: 'afafcq4t01', name: '王者荣耀' },
  { id: 'afafcq4t01', name: '原神' },
  { id: 'afafcq4t01', name: '三国志' },
])

let obj = reactive({ x: 999 })
console.log(car)
console.log(obj)
//方法
function changePrice() {
  car.value.price += 10
  console.log(car.value.price)
  // 用ref的时候，不要忘记.value

  // ref的底层逻辑是reactive
}

function changeFirstGame() {
  games.value[0]!.name = '流星蝴蝶剑'
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
