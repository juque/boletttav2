<script setup>

const emit = defineEmits(['change']);

const handleInput = (event) => {
  let value = event.target.value;
  value = value.replace(/[^\d]/g, '');
  emit('change', value);
  event.target.value = value;
}

</script>

<template>
  <div>
    <form autocomplete="off">
      <label for="input">$</label>
      <input @input="handleInput" type="text" name="input" id="input" pattern="\d*" />
    </form>
  </div>
</template>

<style scoped>
</style>

