<script setup lang="ts">
defineProps({
  link: {
    type: Object
  }
})
</script>

<template>
  <a :href="link.link" target="_blank"
     class="bg-white flex items-center rounded-full p-4 w-full mx-4 max-w-md shadow-lg shadow-red-500">
    <Icon :name="`mdi:${link.icon}`" size="32" class="text-red-600 -mr-8"/>
    <p class="font-bold px-2 m-auto">
      {{ link.text }}
    </p>
  </a>
</template>