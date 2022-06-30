<template>
  <div>
    <!-- 需求：将数组arr的内容渲染到ul中
    v-for 循环数据 每循环一次 生成对应的dom元素
    key：唯一值 类型string/number 提高性能 -->
    <ul>
      <!-- item 数组里边的每一个元素 -->
      <li v-for="item in arr" :key="item">{{ item }}</li>
      <li v-for="(item,index) in arr" :key="index">{{ item }} - {{index}}</li>
      <!-- item 数组里边的每一个元素 index是索引值-->
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: ['迪丽热巴', '赛文', '小哪吒', '泰罗'],
    };
  },
};
</script>

<style></style>
