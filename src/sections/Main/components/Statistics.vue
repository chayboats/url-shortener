<template>
  <Stack class="statistics">
    <Stack style="text-align: center">
      <span class="h2">Advanced Statistics</span>
      <span class="stat-content"
        >Track how your links are performing across the web with out advanced statistics
        dashboard</span
      >
    </Stack>
    <Stack style="justify-content: center; align-items: center">
      <hr class="line" />
      <Columns gap="var(--space-lg)" class="stat-cards" columns="1fr 1fr 1fr">
        <Card
          v-for="card in cardInfo"
          :key="card.key"
          :style="{ transform: `translateY(${card.key}rem)` }"
          class="stat-card"
        >
          <template #icon>
            <Stack class="icon-bg">
              <Icon class="card-icon" :name="card.icon" />
            </Stack>
          </template>
          <template #heading>
            <span class="stat-heading">{{ card.heading }}</span>
          </template>
          <template #content>
            <span class="stat-content">{{ card.content }}</span>
          </template>
        </Card>
      </Columns>
    </Stack>
  </Stack>
</template>

<script setup>
import { Stack, Card, Columns, Icon } from '@/components'

const cardInfo = [
  {
    key: 0,
    icon: 'graph',
    heading: 'brand recognition',
    content:
      "Boast your brand recognition with each click. Generic links don't mean a thing. Branded links help instil confidence in your content."
  },
  {
    key: 1,
    icon: 'guage',
    heading: 'detailed records',
    content:
      'Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.'
  },
  {
    key: 2,
    icon: 'supplies',
    heading: 'fully customizable',
    content:
      'Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.'
  }
]
</script>

<style scoped>
.statistics {
  justify-content: center;
  padding: var(--space-md);
}

.stat-heading {
  font-weight: 700;
  text-transform: capitalize;
}
.stat-content {
  color: var(--color-grey-light);
  font-size: var(--font-size-sm);
}

.stat-cards {
  justify-content: center;
  padding: var(--space-xl) 0;
}

.icon-bg {
  background-color: var(--color-purple-medium);
  padding: var(--space-sm);
  justify-content: center;
  align-items: center;
  width: fit-content;
  border-radius: 100%;
  position: absolute;
  bottom: calc(100% - var(--space-md));
}

.line {
  background-color: var(--color-teal-dark);
  width: 50%;
  position: absolute;
  z-index: 0;
  height: 0.2rem;
  border: none;
}

@media (max-width: 768px) {
  .line {
    height: 30%;
    width: 0.2rem;
  }
}
</style>
