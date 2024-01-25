<script setup>
import { computed } from 'vue';

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

	const formattedGross = computed(() => {
		const grossValue = resultGross();
    const formattedValue = new Intl.NumberFormat('es-CL', {
			style: 'currency',
      currency: 'CLP'
		}).format(grossValue);
		return formattedValue;
	});

	const formattedNet = computed(() => {
		const netValue = resultNet();
    const formattedValue = new Intl.NumberFormat('es-CL', {
			style: 'currency',
      currency: 'CLP'
		}).format(netValue);
		return formattedValue;
	});

	const formattedMakeNet = computed(() => {
		const formatted = new Intl.NumberFormat('es-CL', {
			style: 'currency',
      currency: 'CLP'
		}).format(props.state.input);
		return formatted;

	})

</script>

<template>
  <div>
    <h1>Retencion: {{ parseFloat(props.state.retention) }}%</h1>
    <div class="net">NET: Deberás hacer la boleta por {{ formattedNet }} y recibirás: {{ formattedMakeNet }}</div>
    <div class="gross">GROSS: Deberás hacer la boleta por {{ formattedMakeNet }} y recibirás {{ formattedGross }}</div>
  </div>
</template>

<style scoped>
</style>
