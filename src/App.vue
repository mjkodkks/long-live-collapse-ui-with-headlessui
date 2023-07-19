<script setup lang="ts">
import { ref } from 'vue';
import Collapse from './components/Collapse.vue';

const lists = ref([
  {
    label: 'What is your refund policy?',
    content: `If you're unhappy with your purchase for any reason, email us within
          90 days and we'll refund you in full, no questions asked.`,
  },
  {
    label: 'Lorem Ipsum is simply dummy text',
    content: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been `,
  },
  {
    label: 'Simply dummy text of the printing ',
    content: `If you're unhappy Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been `,
  },
]);
</script>

<template>
  <div class="max-w-screen-sm mx-auto">
    <Collapse :collapseLists="lists"></Collapse>
  </div>
</template>

<style scoped></style>
