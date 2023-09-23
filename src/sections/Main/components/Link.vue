<template>
  <Columns columns="5fr 1fr 1fr" gap="0" class="link">
    <span class="long-link">{{ long }}</span>
    <span class="short-link" style="color: var(--color-teal-dark)">{{ short }}</span>
    <div class="btn-container">
      <Button
        class="copy-btn"
        :style="`background-color: ${buttonColor}`"
        @handle-click="copyLink"
        >{{ buttonText }}</Button
      >
    </div>
  </Columns>
</template>

<script setup>
import { Columns, Button } from '@/components'

import { ref } from 'vue'

const props = defineProps({
  long: { type: String, required: true },
  short: { type: String, required: true }
})

const buttonText = ref('Copy')
const buttonColor = ref(undefined)

async function copyLink() {
  try {
    await navigator.clipboard.writeText(props.short)
    buttonText.value = 'Copied!'
    buttonColor.value = 'var(--color-purple-medium)'
  } catch (error) {
    buttonText.value = 'Failed!'
    buttonColor.value = 'var(--color-error-dark)'
  }
}
</script>

<style scoped>
.short-link {
  margin: var(--space-sm) 0;
}
.link {
  background-color: var(--color-white);
  border-radius: var(--space-xxs);
  align-items: center;
}

.long-link {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  margin: var(--space-sm);
}
.btn-container {
  margin: var(--space-sm);
}

@media (max-width: 768px) {
  .copy-btn {
    width: 100%;
  }
  .short-link {
    border-top: 1.5px solid var(--color-white-dark);
    padding-top: var(--space-sm);
    margin: 0;
  }
}
</style>
