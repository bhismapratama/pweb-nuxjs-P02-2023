<script lang="ts" setup>
import Empty from '../blog/empty.vue'
import cardVue from '../blog/card.vue'

const { data } = await useAsyncData('recent-post', () =>
  queryContent('/blogs').limit(3).sort({ _id: -1 }).find(),
)

const formatedData = computed(() => {
  return data.value?.map((articles) => {
    return {
      path: articles._path,
      title: articles.title || 'no-title available',
      description: articles.description || 'no-descriptoin available',
      image: articles.image || '/',
      alt: articles.alt || 'no alter data available',
      ogImage: articles.ogImage || '/',
      date: articles.date || 'not-date-available',
      tags: articles.tags || [],
      published: articles.published || false,
    }
  })
})

useHead({
  title: 'Home',
  meta: [
    {
      name: 'description',
      content:
        'praktikum haha hihi batiba fp',
    },
  ],
  titleTemplate: 'FP haha hihi - %s',
})
</script>

<template>
  <div class="pb-10">
    <div class="px-6">
      <div class="flex flex-row items-center space-x-3 pt-5 py-5">
        <Icon name="😋" size="2rem" class="text-black dark:text-zinc-300  " />
        <h2 class="text-4xl font-semibold text-black dark:text-zinc-300   ">
          Recent Post
        </h2>
      </div>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
      <template v-for="post in formatedData" :key="post.title">
        <cardVue
          :path="post.path"
          :title="post.title"
          :date="post.date"
          :description="post.description"
          :image="post.image"
          :alt="post.alt"
          :og-image="post.ogImage"
          :tags="post.tags"
          :published="post.published"
        />
      </template>
      <template v-if="data?.length === 0">
        <Empty />
      </template>
    </div>
  </div>
</template>
