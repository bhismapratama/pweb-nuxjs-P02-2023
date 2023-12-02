<script lang="ts" setup>
import topicVue from '~/components/category/topic.vue'
import BlogCard from '~/components/blog/card.vue'
import BlogEmpty from '~/components/blog/empty.vue'

const route = useRoute()

// take category from route params & make first char upper
const category = computed(() => {
  const name = route.params.category || ''
  let strName = ''

  if (Array.isArray(name))
    strName = name.at(0) || ''
  else strName = name
  return strName
})

const { data } = await useAsyncData(`category-data-${category.value}`, () =>
  queryContent('/blogs')
    .where({ tags: { $contains: category.value } })
    .find(),
)

const formattedData = computed(() => {
  return data.value?.map((articles) => {
    return {
      path: articles._path,
      title: articles.title || 'no-title available',
      description: articles.description || 'no-description available',
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
  title: category.value,
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
    <topicVue>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
        <BlogCard
          v-for="post in formattedData"
          :key="post.title"
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
        <BlogEmpty v-if="data?.length === 0" />
      </div>
    </topicvue>
  </main>
</template>
