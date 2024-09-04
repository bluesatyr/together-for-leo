<template>
  <div v-if="isVisible" class="fixed inset-0 bg-gray-800 bg-opacity-75 flex items-center justify-center">
    <div class="bg-white rounded-lg shadow-xl p-6 max-w-lg w-96">
      <button @click="closeModal" class="ml-auto block text-gray-500 hover:text-gray-700 text-xl">&times;</button>
      <div v-html="content"></div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  content: String,
  isVisible: Boolean
});

const emit = defineEmits(['close']);

const closeModal = () => {
  emit('close');
};
</script>

<style scoped>
</style>
