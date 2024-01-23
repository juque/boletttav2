<script setup>

import { reactive, computed } from 'vue';

import Form from "./components/Form.vue";
import Retention from "./components/Retention.vue";
import Result from "./components/Result.vue";

const mapper = [
  {value: "2024", percentage: "13.75", checked: true},
  {value: "2023", percentage: "13", checked: false},
]

const state = reactive({
  input: 0,
  retention: parseFloat(mapper.find(x => x.checked).percentage)
});

const handleInput = (value) => {
  state.input = value;
}

const handleRetentionClick = (value) => {
  state.retention = value;
}

const processedNet = computed(() => {
  return computedNet(state.input) || 0;
});

const processedGross = computed(() => {
  return computedGross(state.input) || 0;
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
  <Retention :mapper="mapper" @change="handleRetentionClick" />
  <Result :state="state" :net="processedNet" :gross="processedGross" />
</template>

<style scoped>
</style>
