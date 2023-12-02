<script lang="ts" setup>
import heroVue from '~/components/main/hero.vue'
import recentVue from '~/components/main/recent.vue'
import trendingVue from '~/components/main/trending.vue'

useHead({
  title: 'Home',
  meta: [
    {
      name: 'description',
      content:
        'haha hihi batiba fp',
    },
  ],
  titleTemplate: 'Maunya si FP - %s',
})

defineOgImage({
  title: 'Maunya si FP',
  description: 'padahal haha hihi batiba fp',
})
</script>

<template>
  <main class="container max-w-6xl mx-auto text-zinc-600">
    <heroVue />
    <recentVue />
    <trendingVue />
  </main>
</template>
