<!-- 官网建议：计算属性的返回值应该被视为只读的，并且永远不应该被更改,应该更新它所依赖的源状态以触发新的计算 -->
<script lang="ts" setup>
defineOptions({
  name: 'Person123',
})

import { ref, computed } from 'vue'

// 数据
let firstName = ref('zhang')
let lastName = ref('san')

// 计算属性（有缓存）
// 这么定义的fullName是一个计算属性，且是只读的(修改姓名会重新计算，重新return)
// let fullName = computed(() => {
//   console.log(1)
//   return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + '-' + lastName.value
// })

// 这么定义的fullName是一个计算属性，且可读可写的
let fullName = computed({
  get() {
    return (
      firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + '-' + lastName.value
    )
  },
  set(val) {
    const [str1, str2] = val.split('-')
    firstName.value = str1!
    lastName.value = str2!
  },
})

// 方法（无缓存）
function changeFullName() {
  fullName.value = 'li-si'
}
</script>

<template>
  <div class="person">
    <!-- v-bind:可以直接简写成: -->
    <!-- v-bind:是单向绑定，只能从数据流向页面，不能从页面流向数据 -->
    <!-- 姓；<input type="text" v-bind:value="firstname" /><br /> -->

    <!-- v-model:value可以直接简写成v-model= -->
    <!-- v-model是双向绑定，数据可以流向页面，页面可以流向数据 -->
    姓：<input type="text" v-model="firstName" /><br />
    名：<input type="text" v-model="lastName" /><br />

    <button @click="changeFullName">将全名改为li-si</button><br />

    <!-- 屎来的，写这么长是要干什么 -->
    <!-- 全名：<span>{{ firstName.slice(0, 1).toUpperCase() + firstName.slice(1) }}-{{ lastName }}</span><br /> -->
    全名：<span>{{ fullName }}</span>
    <br />
    全名：<span>{{ fullName }}</span>
    <br />
    全名：<span>{{ fullName }}</span>
    <br />
    全名：<span>{{ fullName }}</span>
    <br />
    全名：<span>{{ fullName }}</span>
    <br />
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
