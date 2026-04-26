<template>
  <div v-if="post" class="space-y-12 animate-fade-in">
    <!-- Navigation Back -->
    <UButton 
      to="/" 
      icon="i-heroicons-arrow-left" 
      label="Voltar para o Feed" 
      variant="ghost" 
      color="gray" 
    />

    <article class="space-y-8">
      <!-- Header -->
      <header class="space-y-4">
        <div class="flex items-center gap-3">
          <UBadge v-if="post.type === 'event'" color="primary" variant="solid">EVENTO</UBadge>
          <span class="text-sm text-gray-500">{{ formatDate(post.date) }}</span>
        </div>
        <h1 class="text-4xl md:text-6xl font-black text-gray-900 leading-tight">
          {{ post.title }}
        </h1>
        <div v-if="post.location" class="flex items-center gap-2 text-orange-600 font-semibold">
          <UIcon name="i-heroicons-map-pin" />
          <span>{{ post.location }}</span>
        </div>
      </header>

      <!-- Main Image -->
      <div class="rounded-3xl overflow-hidden shadow-2xl border-8 border-white aspect-video md:aspect-[21/9]">
        <img :src="post.image" :alt="post.title" class="w-full h-full object-cover" />
      </div>

      <!-- Content -->
      <div class="prose prose-orange lg:prose-xl max-w-none text-gray-700 leading-relaxed bg-white p-8 rounded-3xl shadow-sm border border-gray-100" v-html="post.content">
      </div>
    </article>

    <!-- Share Section (Simulated) -->
    <section class="border-t border-gray-100 pt-8 flex flex-col md:flex-row items-center justify-between gap-6">
      <div class="flex items-center gap-4">
        <UAvatar src="https://marauecapoeira.com.br/wp-content/uploads/2023/06/m4-1.jpg" alt="Marauê" size="lg" />
        <div>
          <p class="font-bold text-gray-900">Grupo Marauê</p>
          <p class="text-sm text-gray-500">Publicado em {{ formatDate(post.date) }}</p>
        </div>
      </div>
      <div class="flex gap-2">
        <UButton icon="i-heroicons-share" label="Compartilhar" color="primary" variant="soft" />
        <UButton icon="i-heroicons-bookmark" color="gray" variant="ghost" />
      </div>
    </section>
  </div>

  <div v-else class="text-center py-20">
    <h2 class="text-2xl font-bold text-gray-800">Post não encontrado</h2>
    <UButton to="/" label="Voltar para o início" color="primary" class="mt-4" />
  </div>
</template>

<script setup>
import postsData from '~/assets/posts.json'

const route = useRoute()
const post = postsData.find(p => p.slug === route.params.slug)

const formatDate = (dateString) => {
  return new Date(dateString).toLocaleDateString('pt-BR', {
    day: 'numeric',
    month: 'long',
    year: 'numeric'
  })
}

if (post) {
  useSeoMeta({
    title: `${post.title} | Grupo Marauê`,
    description: post.description,
    ogImage: post.image
  })
}
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.5s ease-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>
