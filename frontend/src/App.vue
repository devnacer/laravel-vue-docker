<script setup>
import { ref, onMounted } from 'vue'

const message = ref('Loading...')

onMounted(async () => {
  const res = await fetch('http://10.145.231.81:4555/api/hello')  
  const data = await res.json()
  message.value = data.message + ' (' + data.container + ')'
})
</script>

<template>
  <h1>{{ message }}</h1>
</template>
