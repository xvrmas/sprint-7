<template>
  <div>
    <h3 class="mt-3 ml-3">{{text1}}</h3><br>
    <h3 class="ml-3">{{text2}}</h3>
  </div>
</template>
<script>
export default {
  name: "presupostList",
  props:['text1','text2']
};
</script>
<style>
</style>