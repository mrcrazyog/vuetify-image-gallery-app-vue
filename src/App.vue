<template>
  <VApp>
    <Sidebar @select-option="onSelectOption" />
    <VMain>
      <ImageGallery :isWithColor="isColored" />
    </VMain>
  </VApp>
</template>

<script setup>
import Sidebar from './components/Sidebar.vue';
import ImageGallery from './components/ImageGallery.vue';
import { ref } from 'vue';
const isColored = ref(true);

const onSelectOption = (option) => {
  isColored.value = option;
};
</script>
