<script setup lang="ts">
const route = useRoute()

</script>

<template>
  <p>hello {{ $route.params.id }}</p>
</template>