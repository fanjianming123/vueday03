<template>
  <div>
    <h1>{{obj.a}}</h1>
    <button @click="change">点击我</button>
  </div>
</template>

<script>
//响应式
//数据变化 ==》 视图直接更新
//视图 ==》 数据更新
export default {
  data() {
    return {
      obj:{
        b:10,
        c:12
      }
    }
  },
  methods: {
   change(){
    //方法一：
    // this.obj = {
    //     a:10,
    //     b:10,
    //     c:12
    // }
    // console.log(this.obj);
    //方法二：
    this.$set(this.obj,"a",10)//此处a需要加引号，不加引号则为变量
    console.log(this.obj);
   }
  },
}
</script>

<style>

</style>
