<template>
  <div class="space-y-12">
    <!-- Hero/Header Section -->
    <section class="relative rounded-[2.5rem] overflow-hidden bg-slate-900 mb-16 shadow-2xl shadow-orange-900/20 group">
      <!-- Background Image with Overlay -->
      <div class="absolute inset-0">
        <img 
          src="https://images.unsplash.com/photo-1555597673-b21d5c935865?q=80&w=2000&auto=format&fit=crop" 
          alt="Capoeira Background" 
          class="w-full h-full object-cover opacity-60 group-hover:scale-105 transition-transform duration-700"
        />
        <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-slate-900/40 to-transparent"></div>
      </div>

      <!-- Hero Content -->
      <div class="relative px-8 py-20 md:py-32 text-center space-y-8">
        <UBadge color="primary" variant="subtle" size="lg" class="rounded-full px-4 py-1.5 font-bold tracking-wider uppercase">Tradição & Movimento</UBadge>
        
        <div class="space-y-4">
          <h1 class="text-5xl md:text-7xl font-black tracking-tighter text-white leading-[0.9]">
            Grupo de Capoeira <br/>
            <span class="text-transparent bg-clip-text bg-gradient-to-r from-orange-400 to-orange-600">Marauê</span>
          </h1>
          <p class="text-xl md:text-2xl text-slate-300 max-w-2xl mx-auto font-medium leading-relaxed">
            Preservando a cultura através da arte e do movimento em Bombinhas - SC.
          </p>
        </div>

        <div class="flex flex-col sm:flex-row items-center justify-center gap-4 pt-4">
          <UButton 
            label="Conheça nossas aulas" 
            size="xl" 
            color="primary" 
            class="rounded-full px-10 py-4 font-bold shadow-xl shadow-orange-500/20 hover:scale-105 transition-transform"
            icon="i-heroicons-sparkles"
          />
          <UButton 
            label="Sobre o Grupo" 
            variant="ghost" 
            size="xl" 
            class="rounded-full px-10 py-4 font-bold text-white hover:bg-white/10"
          />
        </div>
      </div>
    </section>

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
