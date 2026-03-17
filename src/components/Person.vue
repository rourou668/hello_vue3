<!-- 若需要一个基本类型的响应式数据，必须使用ref -->
<!-- 若需要一个响应式对象，层级不深，ref、reactive都可以 -->
<!-- 若需要一个响应式对象，且层级较深，推荐使用reactive -->

<script lang="ts" setup>
defineOptions({
  name: 'Person123', //组件名
})

import { reactive, ref } from 'vue'
//数据
let car = reactive({ brand: '奔驰', price: 100 }) //reactive重新分配一个新对象，会失去响应式（可以使用Object.assign去整体替换）
let sum = ref(0)

//方法
function changePrice() {
  car.price += 10
}

function changeBrand() {
  car.brand = '宝马'
}

function changeCar() {
  //这么写页面不更新
  // car = { brand: '法拉利', price: 1000 } ,但是ref可以直接这么写，记得加.value
  // car = reactive({ brand: '法拉利', price: 1000 })

  //页面可以更新
  Object.assign(car, { brand: '法拉利', price: 1000 })
  //Object.assign(a,b,c)
  //把b、c中的属性都加到a中
}

function changeSum() {
  sum.value += 1
}
</script>

<template>
  <div class="person">
    <h2>汽车信息：一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
    <button @click="changePrice">修改汽车的价格</button>
    <button @click="changeBrand">修改汽车的品牌</button>
    <button @click="changeCar">修改汽车</button>
    <h2>当前求和为{{ sum }}</h2>
    <button @click="changeSum">点我sum+1</button>
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
