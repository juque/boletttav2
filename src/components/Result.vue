<script setup>
  const props = defineProps({
    net: Number,
    gross: Number,
    state: Object,
  })

  const resultNet = function(){
    return Math.round(props.state.input * 100 / ( 100 - parseFloat( props.state.retention ) ));
  }

  const resultGross = function(){
    return Math.round( props.state.input * ( 1 - parseFloat( props.state.retention ) / 100) );
  }
</script>

<template>
  <div>
    <h1>Retencion: {{ parseFloat(props.state.retention) }}%</h1>
    <div class="net">NET: {{ resultNet() }}</div>
    <div class="gross">GROSS: {{ resultGross() }}</div>
  </div>
</template>

<style scoped>
</style>
