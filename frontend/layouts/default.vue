<script lang="ts" setup>
import MainHeader from '~/components/main/header.vue'
import MainFooter from '~/components/main/footer.vue'
</script>

<template>
  <div class="gd-container font-poppins">
    <header class="fixed w-full bg-[#F1F2F4] dark:bg-[#151818] z-10">
      <MainHeader />
    </header>
    <main>
      <div class="p-9" />
      <slot />
    </main>
    <footer>
      <MainFooter />
    </footer>
  </div>
</template>

<style scoped>
.gd-container {
  display: grid;
  grid-template-rows: 1fr auto;
  min-height: 100vh;
}
</style>
