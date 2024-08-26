<template>
  <v-container >
    <v-data-table
      :headers="headers"
      :items="items"
      class="elevation-1"
    >
      <template v-slot:item.description="{ item }">
        <TruncateText :text="item.description" :maxLength="30" />
      </template>
    </v-data-table>
  </v-container>
</template>

<script setup>
import { ref } from 'vue';
import TruncateText from './TruncateText.vue';

const headers = ref([
  { text: 'Name', value: 'name' },
  { text: 'Description', value: 'description' },
  { text: 'Price', value: 'price' },
]);

const items = ref([
  {
    name: 'Product 1',
    description:
      'This is a very long description that should be truncated in the table view but fully visible in the tooltip.',
    price: '$10',
  },
  {
    name: 'Product 2',
    description:
      'Another long description that needs to be shortened for display purposes.',
    price: '$15',
  },
  {
    name: 'Product 3',
    description:
      'Another long.',
    price: '$25',
  },
  {
    name: 'Product 4',
    description:
      'Another long assasa saaaaaa saaaaaaaaaaa assssssssss assssssssssssss asssssss.',
    price: '$25',
  },
  {
    name: 'Product 5',
    description:
      'Another longsadasasadsassssssssssssssssssssssssssssssssssssssssssssssssssssssssssss.',
    price: '$25',
  },
  // Add more items as needed
]);
</script>
