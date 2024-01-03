<script setup>
  const props = defineProps({
    net: Number,
    gross: Number,
  })
</script>

<template>
  <div>
    <div class="net">NET: {{ props.net }}</div>
    <div class="gross">GROSS: {{ props.gross }}</div>
  </div>
</template>

<style scoped>
</style>
