<template>
  <div
    v-if="visible"
    class="relative w-full max-w-[450px] flex items-center gap-3 p-3 bg-emerald-500 border border-emerald-700 text-white rounded-md shadow-md"
  >
    <div>
        <img :src="infoSVG" class="w-[20px] h-[20px] fill-white" alt="">
    </div>
    <div class="flex-1">
      {{ message }}
    </div>
    <button
      @click="closeBanner"
      class="absolute top-0 right-3 bg-transparent border-none text-white text-lg font-bold hover:opacity-80 focus:outline-none p-0 cursor-pointer"
      aria-label="Close notification"
    >
      &times;
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import infoSVG from '../assets/info.svg';
// Props
const props = defineProps({
  message: {
    type: String,
    required: true,
  },
});

const visible = ref(true);

const closeBanner = () => {
  visible.value = false;
};
</script>

<style scoped>
</style>
