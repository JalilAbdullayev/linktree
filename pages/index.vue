<script setup lang="ts">
interface Link {
  link: string,
  text: string,
  icon: string
}

const links: Link[] = [
  {
    link: 'https://youtube.com/@Jalil_Abdullayev',
    text: 'YouTube',
    icon: 'youtube'
  },
  {
    link: 'https://instagram.com/jalil_abdullayev_',
    text: 'Instagram',
    icon: 'instagram'
  },
  {
    link: 'https://linkedin.com/in/jalil-abdullayev/',
    text: 'LinkedIn',
    icon: 'linkedin'
  }
];
</script>

<template>
  <div class="bg-gradient-to-br from-red-400 to-sky-200 w-screen h-screen">
    <div class="flex justify-center items-center pt-4">
      <Avatar/>
    </div>
    <div class="text-center text-lg font-medium mt-2 pb-4 text-white">
      <h1>
        Full Stack Web Developer
      </h1>
      <h2>
        Jalil Abdullayev
      </h2>
    </div>
    <div class="flex flex-col items-center px-4">
      <CardLinks v-for="(link, index) in links" :key="index" :link="link" class="mt-6"/>
    </div>
    <Share/>
  </div>
</template>
