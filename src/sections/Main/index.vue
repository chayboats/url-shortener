<template>
  <Stack class="main">
    <Form :error="error" @submit="handleSubmit" @click="resetError" />
    <Stack reverse class="links">
      <Link
        v-for="link in links"
        :key="links.indexOf(link)"
        :long="link.longLink"
        :short="link.shortLink"
      />
    </Stack>
    <Statistics />
    <Boost />
  </Stack>
</template>

<script setup>
import { ref } from 'vue'
import Form from './components/Form.vue'
import Statistics from './components/Statistics.vue'
import Boost from './components/Boost.vue'
import Link from './components/Link.vue'
import { Stack } from '@/components'

const links = ref(JSON.parse(getLocalLinks()))
const error = ref(false)
const input = ref(undefined)

async function fetchLink(urlInput) {
  const link = await fetch(`https://api.shrtco.de/v2/shorten?url=${urlInput}`)
  const jsonLink = await link.json()
  return jsonLink.result.short_link
}

async function handleSubmit(urlInput) {
  try {
    const shortLink = await fetchLink(urlInput)
    links.value.push({ longLink: urlInput, shortLink })
    localStorage.setItem('links', JSON.stringify(links.value))
  } catch (err) {
    error.value = true
  } finally {
    resetInput()
  }
}

function getLocalLinks() {
  if (!localStorage.getItem('links')) {
    localStorage.setItem('links', JSON.stringify([]))
  }
  return localStorage.getItem('links')
}

function resetError() {
  if (error.value) {
    error.value = false
  }
}

function resetInput() {
  if (!input.value) {
    input.value = document.getElementById('url-input')
  }
  if (!error.value) {
    input.value.value = ''
  }
  input.value.blur()
}
</script>

<style scoped>
.main {
  background-color: var(--color-white-dark);
  position: relative;
}
.links {
  padding: 5rem 6rem 0;
}

@media (max-width: 768px) {
  .links {
    padding: 8rem var(--space-md) 0;
  }
  .form-background {
    margin: 0 var(--space-md);
    bottom: calc(100% - 4.5rem);
  }
}
</style>
