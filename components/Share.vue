<script setup lang="ts">
let open = ref(false);
</script>

<template>
  <div>
    <p @click="open = true" class="text-center mt-4 font-bold text-blue-600 text-lg cursor-pointer">
      Share
    </p>
    <ShareModal v-model="open"/>
  </div>
</template>