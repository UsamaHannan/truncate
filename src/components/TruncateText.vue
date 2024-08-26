<template>
    <v-tooltip location="top" :text="fullText">
      <template v-slot:activator="{ props }">
        <span 
          v-if="isTruncated"
          :title="fullText"
          class="truncated-text"
          v-bind="props"
        >
          {{ truncatedText }}
        </span>
        <span v-else>{{ fullText }}</span>
      </template>
    </v-tooltip>
  </template>
  
  <script setup>
  import { computed, defineProps } from 'vue';
  
  const props = defineProps({
    maxLength: {
      type: Number,
      default: 30,
    },
    text: {
      type: String,
      required: true,
    },
  });
  
  const fullText = computed(() => props.text.trim());
  
  const truncatedText = computed(() => {
    return fullText.value.length > props.maxLength
      ? fullText.value.slice(0, props.maxLength) + '...'
      : fullText.value;
  });
  
  const isTruncated = computed(() => fullText.value.length > props.maxLength);
  </script>
  
  <style scoped>
  .truncated-text {
    cursor: pointer;
  }
  </style>
  