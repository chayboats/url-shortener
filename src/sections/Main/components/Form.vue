<template>
  <Row class="form-background">
    <form @submit.prevent="$emit('submit', urlInput)">
      <Columns columns="20fr 1fr" gap="var(--space-xs) var(--space-sm)">
        <input
          id="url-input"
          v-model="urlInput"
          type="text"
          autocomplete="off"
          placeholder="Shorten a link here..."
          @click="$emit('click')"
        />
        <Button style="width: 100%" class="btn-large">Shorten It!</Button>
        <span class="error-msg">Please add a link</span>
      </Columns>
    </form>
  </Row>
</template>

<script setup>

import { Row, Columns, Button } from '@/components'
import { ref } from 'vue'

defineProps({
  error: { type: Boolean, default: false }
})

defineEmits(['submit', 'click'])

const urlInput = ref('')
</script>

<style scoped>
.form-background {
  padding: var(--space-md);
  padding-bottom: var(--space-xs);
  background-color: var(--color-purple-medium);
  background-image: url('../../../assets/images/form-bg-design.svg');
  border-radius: var(--space-xs);
  position: absolute;
  left: 0;
  right: 0;
  margin: 0 6rem;
  bottom: calc(100% - var(--space-lg));
  justify-content: space-around;
}

.error-msg {
  font-size: var(--font-size-sm);
  color: v-bind('error ? "var(--color-error-dark)": "transparent"');
  font-style: italic;
}

::placeholder {
  color: v-bind('error && "var(--color-error-light)"');
}

#url-input {
  outline: v-bind('error && "0.15rem solid var(--color-error-dark)"');
}
</style>
