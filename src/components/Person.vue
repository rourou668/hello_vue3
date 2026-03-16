<!-- 1.setup返回值 -->
<!-- 2.setup与OptionsAPI -->
<!-- setup是最早的生命周期，setup不可以读取data，methods（这两个都是vue2），但他们可以读取setup里的数据 -->

<script lang="ts">
export default {
  name: 'Person',
  data() {
    return {
      a: 100,
      c: this.name,
      d: 900,
    }
  },
  methods: {
    b() {
      console.log('b')
    },
  },
  setup() {
    //数据
    let name = '张三'
    let age = 18
    let tel = '1388888888'
    // let x= d

    // 方法
    function changeName() {
      name = 'zhang-san'
      console.log(name)
    }
    function changeAge() {
      age += 1
    }
    function showTel() {
      alert(tel)
    }
    return { name, age, changeName, changeAge, showTel }

    //setup的返回值
    // return () => '哈哈'
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
    <hr />
    <h2>测试1：{{ a }}</h2>
    <button @click="b">测试2</button>
    <h2>测试3：{{ c }}</h2>
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
