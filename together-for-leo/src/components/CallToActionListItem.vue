<script setup>
  defineProps({
  title: String,
  subtitle: String,
  content: String,
  imageUrl: String,
  bgColor: String,
});

const emit = defineEmits(['showModal']);

const handleClick = () => {
  emit('showModal', { title, subtitle, content });
};
</script>

<template>
  <li @click="handleClick" class="card hover:bg-gray-200">
    <div>
      <div><span class="font-bold">{{ title }}</span>&nbsp;{{ subtitle }}</div>
      <slot></slot>
    </div>
  </li>
</template>