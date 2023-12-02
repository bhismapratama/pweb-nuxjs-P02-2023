<script setup lang="ts">
import connect from '../footer/connect.vue'
import linkVue from '../footer/link.vue'
import devloper from '../footer/devloper.vue'
</script>

<template>
  <div class="py-5 border-t dark:border-gray-800  mt-5 text-zinc-700 dark:text-zinc-300  ">
    <div class="px-6 container max-w-6xl mx-auto">
      <div class="w-full flex justify-between">
        <devloper />
        <linkVue />
        <connect />
      </div>
    </div>
  </div>
</template>

<style>

</style>
