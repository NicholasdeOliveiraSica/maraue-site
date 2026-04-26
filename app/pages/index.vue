<template>
  <div class="space-y-12">
    <!-- Hero/Header Section -->
    <header class="text-center space-y-4 mb-12">
      <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-gray-900">
        Grupo de Capoeira <span class="text-orange-600">Marauê</span>
      </h1>
      <p class="text-lg text-gray-600 max-w-2xl mx-auto">
        Tradição, cultura e movimento em Bombinhas - SC. Explore nossa jornada através da capoeira.
      </p>
    </header>

    <!-- Feed Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <div v-for="post in sortedPosts" :key="post.slug" :class="post.type === 'event' ? 'md:col-span-2' : ''">
        <EventCard v-if="post.type === 'event'" :post="post" />
        <PostCard v-else :post="post" />
      </div>
    </div>

    <!-- Empty State -->
    <div v-if="posts.length === 0" class="text-center py-20">
      <UIcon name="i-heroicons-inbox" class="w-16 h-16 text-gray-300 mx-auto mb-4" />
      <p class="text-gray-500">Nenhum post encontrado.</p>
    </div>
  </div>
</template>

<script setup>
import postsData from '~/assets/posts.json'

const posts = postsData

const sortedPosts = computed(() => {
  return [...posts].sort((a, b) => new Date(b.date) - new Date(a.date))
})

useSeoMeta({
  title: 'Início | Grupo Marauê',
  description: 'Feed de atividades e eventos do Grupo de Capoeira Marauê em Bombinhas - SC.'
})
</script>
