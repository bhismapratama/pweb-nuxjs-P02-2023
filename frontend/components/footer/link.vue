<template>
  <div class="flex flex-col dark:text-zinc-300 items-start my-5 md:my-0 md:justify-self-center">
    <p class="text-black dark:text-zinc-300  text-base font-semibold mb-3">
      Quick Link
    </p>
    <div class="w-[200px] flex justify-between">
      <div class="flex flex-col items-center gap-2">
        <NuxtLink to="/" class="hover:underline">
          Home
        </NuxtLink>
        <NuxtLink to="/blogs" class="hover:underline">
          Blogs
        </NuxtLink>
      </div>
      <div class="flex flex-col items-center gap-2">
        <NuxtLink to="/categories" class="hover:underline">
          Categories
        </NuxtLink>
        <NuxtLink to="/about" class="hover:underline">
          About P02
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
