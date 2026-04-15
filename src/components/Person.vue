<!-- vue3中的watch只能监视以下四中数据 -->
<!-- 1.ref定义的数据 -->
<!-- 2.reactive定义的数据 -->
<!-- 3.函数返回一个值 -->
<!-- 4.一个包含以上内容的数组 -->

<script lang="ts" setup>
defineOptions({
  name: 'Person123',
})

import { ref, watch } from 'vue'

//数据
let sum = ref(0)

// 方法
function changeSum() {
  sum.value += 1
}

// 监视
// watch(谁？，回调函数)
// 注意sum后面不要加.value
const stopWatch = watch(sum, (newValue, oldValue) => {
  console.log('sum变化了', newValue, oldValue)
  if (newValue >= 10) {
    stopWatch()
  }
})
</script>

<template>
  <div class="person">
    <h1>情况一：监视【ref】定义的基本型数据</h1>
    <h2>当前求和为：{{ sum }}</h2>
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
