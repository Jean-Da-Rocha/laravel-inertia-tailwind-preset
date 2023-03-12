<script setup lang="ts">
import { PropType } from 'vue';

const props = defineProps({
  modelValue: {
    type: String as PropType<string>,
  },
  inputType: {
    type: String as PropType<'text' | 'password' | 'email'>,
    default: 'text',
    required: true,
    validator: (value: string) => ['text', 'password', 'email'].includes(value),
  },
  inputErrorMessage: {
    type: String as PropType<string>,
  },
  inputName: {
    type: String as PropType<string>,
    required: true,
  },
  required: {
    type: Boolean as PropType<boolean>,
    default: true,
  },
  placeholder: {
    type: String as PropType<string>,
  },
});

const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void;
}>();

const handleInput = (event: Event) => {
  const target = event.target as HTMLInputElement;
  const value = target.value;

  emit('update:modelValue', value);
};
</script>

<template>
  <input
    :type="props.inputType"
    :name="props.inputName"
    :id="props.inputName"
    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-indigo-600 focus:border-indigo-600 block w-full p-2.5"
    :class="
      props.inputErrorMessage &&
      'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500  focus:border-red-500 block w-full p-2.5'
    "
    :placeholder="props.placeholder"
    :required="props.required"
    @input="handleInput"
  />
  <p class="mt-2 text-sm text-red-600" v-if="props.inputErrorMessage">
    <span class="font-medium">
      {{ props.inputErrorMessage }}
    </span>
  </p>
</template>
