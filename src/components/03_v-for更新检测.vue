<template>
  <div>
    <!-- 观察数组的哪些方法 可以导致vue的视图发生更新 -->
    <ul>
      <li v-for="item in arr" :key="item">{{ item }}</li>
    </ul>
    <button @click="reverse">数组翻转</button>
    <button @click="slice">截取前3个</button>
    <button @click="change">更新第一个元素值</button>
  </div>
</template>

<script>
export default {
  name: 'VuecliDemo02VFor',

  data() {
    return {
      arr: [1, 2, 3, 4, 5],
    };
  },
  mounted() {},
  methods: {
    reverse() {
      this.arr.reverse();
    },
    slice() {
      this.arr = this.arr.slice(0, 3);
    },
    change(){
        this.$set(this.arr,0,888)
    }
  },
};
</script>

<style scoped></style>
