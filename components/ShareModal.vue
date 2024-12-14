<script setup lang="ts">
const url = useRequestURL();
let copy = ref("Copy");
defineProps({
  modelValue: {
    type: Boolean,
    default: false
  }
});

const emits = defineEmits(['update:modelValue']);

const close = () => {
  emits('update:modelValue', false);
  copy.value = 'Copy';
};

const shareLink = () => navigator.clipboard.writeText(url.href).then(() => copy.value = "Copied");
</script>

<template>
  <div :class="modelValue ? 'visible' : 'invisible'">
    <div class="bg-black fixed top-0 start-0 size-full z-20 transition-all duration-300 ease-in-out"
         :class="!modelValue ? 'opacity-0' : 'opacity-30'"></div>
    <div class="fixed start-0 top-0 z-30 size-full flex items-center transition-all duration-300 ease-out"
         :class="!modelValue ? 'opacity-0 -translate-y-12' : 'opacity-100 translate-y-0'">
      <div class="bg-white z-50 m-auto p-4 rounded-lg">
        <div class="flex items-center justify-between mb-10">
          <p class="text-gray-800 font-medium text-lg">
            Share this page
          </p>
          <button @click="close" type="button"
                  class="bg-gray-300 size-7 flex justify-center items-center rounded-full">
            <Icon name="mdi:close" size="20"/>
          </button>
        </div>
        <div class="flex items-center justify-between">
          <div class="flex items-center">
            <Icon name="mdi:whatsapp" size="20" class="text-green-600"/>
            <a :href="`https://wa.me?text=${url.href}`" target="_blank">
            <span class="ml-2 text-gray-800 mr-8">
              Share with WhatsApp
            </span>
            </a>
          </div>
          <Icon name="mdi:chevron-right" size="30" class="text-gray-400"/>
        </div>
        <div class="flex justify-between border-2 border-gray-200 p-2 mt-8 rounded items-center">
          <Icon name="mdi:content-copy"/>
          <p class="mx-4">
            {{ url.href }}
          </p>
          <button class="font-medium" :class="copy === 'Copy' ? 'text-gray-800' : 'text-green-800'" @click="shareLink">
            {{ copy }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>