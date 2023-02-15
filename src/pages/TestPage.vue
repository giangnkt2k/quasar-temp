<template>
  <div>
    {{ counter }}
  </div>
</template>
<script setup>
import { computed } from 'vue';
import { useCounterStore } from 'stores/counter';
import { storeToRefs } from 'pinia';
const store = useCounterStore();

const { counter, doubleCount } = storeToRefs(store); // state and getters need "storeToRefs"
const { increment } = store; // actions can be destructured directly
</script>
