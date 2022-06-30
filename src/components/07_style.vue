<template>
  <div>
    <!-- 动态绑定style 语法 v-bind:style="对象" 
  			v-bind:style = '{css属性名: 值}'-->
    <p :style="{ color, fontSize }">窗前明月光</p>
    <p :style="{ color: 'blue', fontSize: '50px' }">疑是地上霜</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      color: 'red',
      fontSize: '200px',
    };
  },
};
</script>

<style></style>
