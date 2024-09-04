<script setup>
defineProps({
  title: String,
  content: String,
  imageUrl: String,
  bgColor: String,
});
</script>

<template>
  <div class="container mx-auto py-8 px-4" :class="bgColor">
    <h2 class="text-2xl font-semibold mb-2">How You Can Help</h2>
    <slot></slot>
  </div>
</template>

<style scoped>
</style>