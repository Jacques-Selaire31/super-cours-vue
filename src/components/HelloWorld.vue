<script setup>
import { ref } from 'vue'


// defineProps({
//   msg: String,
// })
const props = defineProps(['foo','username'])
</script>

<template>
  <h1>Salut {{ foo }} - {{ username }}</h1>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
