<script setup lang="ts">
defineProps({
  text: {
    type: String,
    default: 'Ура моц первый компонент!',
  },
  count: Number,
})
defineEmits(['countClick'])
</script>

<template>
  <h1>{{ text }}</h1>
  <button @click="$emit('countClick')">{{ count }}</button>
</template>

<style scored>
h1 {
  color: red;
}
</style>
