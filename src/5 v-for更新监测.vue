<template>
  <div>
    <ul>
      <li v-for="(item, index) in arr" :key="index">{{ item }}</li>
    </ul>
    <button @click="revFn">数组翻转</button>
    <button @click="sliceFn">截取前3个</button>
    <button @click="updateFn">更新第一个元素值</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [5, 3, 9, 2, 1],
    };
  },
  methods: {
    revFn() {
      this.arr.reverse();
    },
    sliceFn() {
      this.arr = this.arr.slice(0, 3);
    },
    updateFn() {
      this.$set(this.arr, 0, 100);
    },
  },
};
</script>

<style></style>
