<script lang="ts">
export default {
  name: '',
  setup() {
    //console.log(this)
    //setup函数中的this是undefined,vue3中已经弱化this了
    // 数据，原来是写在data中，此时的name,age,tel都不是响应式数据
    let name = '张三'
    let age = 18
    let tel = '1388888888'

    // 方法
    function changeName() {
      name = 'zhang-san' //这样修改name，页面是没有变化的
      console.log(name) //name确实改了，但name不是响应式的，下面的age，tel也是
    }
    function changeAge() {
      age += 1
    }
    function showTel() {
      alert(tel)
    }
    return { name, age, changeName, changeAge, showTel }
  },
}
</script>

<template>
  <div class="person">
    <h2>姓名:{{ name }}</h2>
    <h2>姓名:{{ age }}</h2>
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
