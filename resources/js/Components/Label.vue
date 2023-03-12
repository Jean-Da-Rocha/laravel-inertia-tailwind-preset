<script setup lang="ts">
import { PropType } from 'vue';

const props = defineProps({
  inputErrorMessage: String as PropType<string>,
  for: String as PropType<string>,
});
</script>

<template>
  <label
    :for="props.for"
    class="block mb-2 text-sm font-medium text-gray-900"
    :class="props.inputErrorMessage && 'block mb-2 text-sm font-medium text-red-700'"
  >
    <slot></slot>
  </label>
</template>
