<script>
import ifgrammar from './components/ifgrammar.vue'
export default {
  data() {
    return {
      msg:"牛魔",
      dynamicClass: "testClass",
      objectOfAttrs: {
        class: "dynamicClass",
        id: "appid"
      },
    }
  }
}
</script>

<template>
<!--  <h3>template</h3>-->
<!--  模版插值-->
<!--  动态绑定-->
<!--  <div v-bind:class="dynamicClass">{{ msg }}</div>-->
<!--  对象绑定-->
<!--  <div v-bind="objectOfAttrs">object</div>-->
<!--  if-->
<ifgrammar/>
</template>

<style>
.testClass{
  color: red;
}
.dynamicClass{
  color: darkgreen;
  font-size: 20px;
}
</style>