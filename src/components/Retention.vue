<script setup>
const emit = defineEmits(['change']);
const handleClick = (event) => {
 emit('change', event.target.value);
}
const props = defineProps({
  mapper: Object
})

</script>

<template>
  <div>
    <template v-for="item in props.mapper" :key="item.value">
      <label>
        <input type="radio" @click="handleClick" name="retention" :value="item.percentage" :checked="item.checked" />{{ item.percentage }}%
      </label>
    </template>
  </div>
</template>

<style scoped>
</style>

