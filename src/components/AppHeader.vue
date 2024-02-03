<script setup>
// defineProps(['color', 'title'])
defineProps(["color"]);
</script>

<template>
  <header class="header">
    <!-- プロップスで値を渡す -->
    <!-- <h1 :style="{color:color}" class="">{{ title }}</h1> -->
    <!-- slotで渡す デフォルトで値を入れることもできる -->
    <h1 :style="{ color: color }" class=""><slot>NoTitle</slot></h1>
  </header>
</template>

<style lang="scss" scoped>
.header {
  h1 {
    font-size: 20px;
    border-bottom: 1px solid #ccc;
  }
}
</style>
