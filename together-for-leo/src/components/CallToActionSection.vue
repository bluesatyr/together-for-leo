<script setup>
defineProps({
  title: String,
  content: String,
  imageUrl: String,
  bgColor: String,
});
</script>

<template>
  <div class="container mx-auto py-8 px-2" :class="bgColor">
    <h2 class="text-2xl font-semibold">How You Can Help</h2>
    <slot></slot>
    <!-- <div class="mt-4">
      <img :src="imageUrl" alt="Image" class="rounded-lg w-full">
    </div> -->
  </div>
</template>

<style scoped>
</style>