<script setup lang="ts">
import type { BlogPost } from '@/types/blog'
import BlogHeader from '~/components/blog/Header.vue'
import BlogToc from '~/components/blog/Toc.vue'

const { path } = useRoute()

const { data: articles, error } = await useAsyncData(`blog-post-${path}`, () => queryContent(path).findOne())

if (error.value)
  navigateTo('/404')

const data = computed<BlogPost>(() => {
  return {
    title: articles.value?.title || 'no-title available',
    description: articles.value?.description || 'no-descriptoin available',
    image: articles.value?.image || '/',
    alt: articles.value?.alt || 'no alter data available',
    ogImage: articles.value?.ogImage || '/',
    date: articles.value?.date || 'not-date-available',
    tags: articles.value?.tags || [],
    published: articles.value?.published || false,
  }
})

useHead({
  title: data.value.title || '',
  meta: [
    { name: 'description', content: data.value.description },
    {
      name: 'description',
      content: data.value.description,
    },
    { property: 'og:site_name', content: 'FP haha hihi' },
    { hid: 'og:type', property: 'og:type', content: 'website' },
    {
      property: 'og:url',
      content: 'hehe',
    },
    {
      property: 'og:title',
      content: data.value.title,
    },
    {
      property: 'og:description',
      content: data.value.description,
    },
    {
      property: 'og:image',
      content: data.value.ogImage || data.value.image,
    },
  ],
})

defineOgImage({
  title: data.value.title,
  description: data.value.description,
})
</script>

<template>
  <div class="px-6 container max-w-6xl mx-auto sm:grid grid-cols-12 gap-x-12 ">
    <div class="col-span-12 lg:col-span-9">
      <BlogHeader
        :title="data.title"
        :image="data.image"
        :alt="data.alt"
        :date="data.date"
        :description="data.description"
        :tags="data.tags"
      />
      <div
        class="prose prose-pre:max-w-xs sm:prose-pre:max-w-full prose-sm sm:prose-base md:prose-lg
        prose-h1:no-underline max-w-5xl mx-auto prose-zinc dark:prose-invert prose-img:rounded-lg"
      >
        <ContentRenderer v-if="articles" :value="articles">
          <template #empty>
            <p>Tidak ada content.</p>
          </template>
        </ContentRenderer>
      </div>
    </div>
    <BlogToc />
  </div>
</template>
