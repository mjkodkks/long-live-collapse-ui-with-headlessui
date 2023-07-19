<template>
  <div class="w-full rounded-2xl bg-white p-2 flex gap-2 flex-col">
    <Disclosure
      v-slot="{ open }"
      v-for="collapseList in collapseLists"
      :key="collapseList.label"
    >
      <DisclosureButton
        class="
          flex
          w-full
          justify-between
          rounded-lg
          bg-purple-100
          px-4
          py-2
          text-left text-sm
          font-medium
          text-purple-900
          hover:bg-purple-200
          focus:outline-none
          focus-visible:ring
          focus-visible:ring-purple-500
          focus-visible:ring-opacity-75
        "
      >
        <span v-if="collapseList.label">{{ collapseList.label }}</span>
        <!-- <ChevronUpIcon
            :class="open ? 'rotate-180 transform' : ''"
            class="h-5 w-5 text-purple-500"
          /> -->
      </DisclosureButton>
      <TransitionRoot
        :show="open"
        enter="transition-all duration-700"
        enter-from="max-h-0 opacity-0"
        enter-to="max-h-[500px] opacity-100"
        leave="transition-all duration-500"
        leave-from="max-h-[500px] opacity-100"
        leave-to="max-h-0 opacity-0"
      >
        <DisclosurePanel static class="px-4 pb-2 text-sm text-gray-500">
          <span v-if="collapseList.content">
            {{ collapseList.content }}
          </span>
        </DisclosurePanel>
      </TransitionRoot>
    </Disclosure>
  </div>
</template>

<script setup lang="ts">
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue';
import { TransitionRoot } from '@headlessui/vue';
import { defineProps } from 'vue';

const props = defineProps({
  collapseLists: {
    type: Array,
    validator: (value) => {
      // Custom validation rules
      // Return true if the value is valid, or false otherwise
      return Array.isArray(value) && value.length > 0;
    },
  },
});
</script>

<style scoped></style>
