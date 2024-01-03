<script setup>

import { ref, computed } from 'vue';

import Form from "./components/Form.vue";
import Retention from "./components/Retention.vue";
import Result from "./components/Result.vue";

const inputValue = ref(0);

const handleInput = (value) => {
  inputValue.value = value;
}

const processedNet = computed(() => {
  return computedNet(inputValue.value) || 0;
});

const processedGross = computed(() => {
  return computedGross(inputValue.value) || 0;
});

const computedNet = (value) => {
  return parseInt(value);
}

const computedGross = (value) => {
  return parseInt(value);
}


</script>

<template>
  <h1>Bolettta</h1>
  <h2>Calcula tu boleta de honorarios</h2>
  <Form @change="handleInput" />
  <Retention />
  <Result :net="processedNet" :gross="processedGross" />
</template>

<style scoped>
</style>
