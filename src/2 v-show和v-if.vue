<template>
  <div>
    <h1 v-show="isShow">我是show</h1>
    <h2 v-if="isIf">我是if</h2>
    <p v-if="age >= 18">成年</p>
    <p v-else>未成年</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
      isIf: true,
      age: 18,
    };
  },
};
</script>

<style></style>
