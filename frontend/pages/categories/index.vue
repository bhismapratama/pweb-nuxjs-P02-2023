<script lang="ts" setup>
import heroVue from '~/components/category/hero.vue'
import cardVue from '~/components/category/card.vue'
import { makeFirstCharUpper } from '@/utils/helper'

const topics = [
  'Javascript',
  'Typescript',
  'Git',
  'Next js',
  'MongoDB',
  'MySQL',
  'PhpMyAdmin',
  'Vercel',
]

useHead({
  title: 'Categories',
  meta: [
    {
      name: 'description',
      content:
        'praktikum haha hihi batiba fp',
    },
  ],
  titleTemplate: 'FP haha hihi - %s',
})

defineOgImage()
</script>

<template>
  <main class="container max-w-6xl mx-auto text-zinc-600">
    <heroVue />
    <div class="flex flex-wrap px-6 mt-12 gap-3">
      <cardVue v-for="topic in topics" :key="topic" :title="makeFirstCharUpper(topic)" />
    </div>
  </main>
</template>
