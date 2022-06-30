<template>
  <div>
    <!-- 动态绑定style 语法 v-bind:style="对象" 
  			v-bind:style = '{css属性名: 值}'-->
    <p v-bind:style="{ color: 'red', fontSize: '30px' }">vue 动态绑定style11</p>
    <p :style="{ color: colorValue, fontSize: fontSize + 'px' }">
      vue 动态绑定style22
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      colorValue: 'green',
      fontSize: 22,
    };
  },
};
</script>

<style></style>
