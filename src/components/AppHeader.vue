<script setup>
  // defineProps(['color', 'title'])
  defineProps(['color'])
</script>

<template>
  <header>
    <!-- プロップスで値を渡す -->
    <!-- <h1 :style="{color:color}" class="">{{ title }}</h1> -->
    <!-- slotで渡す デフォルトで値を入れることもできる -->
    <h1 :style="{color:color}" class=""><slot>NoTitle</slot></h1>

  </header>
</template>
