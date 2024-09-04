<script setup>
const props = defineProps({
  title: String,
  subtitle: String,
  description: String,
  content: String,
  imageUrl: String,
  bgColor: String,
});

const emit = defineEmits(['showModal']);

const handleClick = () => {
  emit('showModal', { 
    title: props.title, 
    subtitle: props.subtitle, 
    content: props.content 
  });
};
</script>

<template>
  <li @click="handleClick" class="card hover:bg-gray-200 border-2 rounded mb-2">
    <div>
      <div><span class="font-bold">{{ title }}</span>&nbsp;{{ subtitle }}</div>
      <div>{{ description }}</div>
    </div>
  </li>
</template>
