<template>
  <Stack class="get-started">
    <span class="h2">Boost your links today</span>
    <Button class="btn-large-round">Get Started</Button>
  </Stack>
</template>

<script setup>
import { Stack, Button } from '@/components'
</script>

<style scoped>
.get-started {
  background-image: url('../../../assets/images/boost-bg-design.svg');
  background-color: var(--color-purple-medium);
  color: var(--color-white);
  text-align: center;
  align-items: center;
  padding: var(--space-md);
}
</style>
