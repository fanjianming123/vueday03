<template>
  <div>
    <p :class="{ active: activeFlag }">我是p标签</p>
    <button @click="activeFlag = !activeFlag">click</button>
    <p class="box" :class="{ active: activeFlag }">我也是p</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeFlag: true,
    };
  },
};
</script>

<style>
.box {
  color: blueviolet;
}
.active {
  color: brown;
}
</style>
