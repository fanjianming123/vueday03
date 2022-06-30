<template>
  <div id="app">
    <ul>
      <li v-for="item in myArr" :key="item">{{item}}</li>
    </ul>
    <button @click="btn">走一走</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myArr: ["帅哥", "美女", "程序猿"],
    };
  },
  methods:{
    btn(){
      //头部数据加到尾部
      this.myArr.push(this.myArr[0])
      //头部数据删除
      this.myArr.shift()
    }
  }
};
</script>

<style>
</style>
