<template>
  <Columns class="hero">
    <Stack class="hero-content">
      <span class="hero-text">More than just shorter links</span>
      <span>
        Build your brand's recognition and get detailed insights on how your links are performing
      </span>
      <Button class="get-started btn-large-round">Get Started</Button>
    </Stack>
    <img class="person-working" src="../assets/images/person-working.svg" />
  </Columns>
</template>

<script setup>
import { Columns, Stack, Button } from '@/components'
</script>

<style scoped>
.hero {
  padding: var(--space-xl);
  overflow-x: hidden;
}
.hero-content {
  min-width: 28rem;
}

.person-working {
  max-width: 30rem;
  height: fit-content;
}

@media (max-width: 768px) {
  .person-working {
    max-width: 25rem;
    padding-bottom: var(--space-lg);
  }
  .get-started {
    margin: auto;
  }
  .hero-content {
    padding: 0 var(--space-sm);
    min-width: min-content;
  }

  .hero {
    justify-content: center;
  }
}
</style>
