<template>
  <UCard 
    class="overflow-hidden border border-orange-100/50 bg-white/40 backdrop-blur-md shadow-sm hover:shadow-2xl hover:shadow-orange-200/50 transition-all duration-500 group cursor-pointer rounded-3xl" 
    @click="navigateTo(`/posts/${post.slug}`)"
    :ui="{ body: { padding: 'p-0' }, header: { padding: 'p-0' } }"
  >
    <template #header>
      <div class="relative overflow-hidden aspect-[16/10] sm:aspect-[4/5]">
        <img 
          :src="post.image" 
          :alt="post.title" 
          class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
        />
        <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
      </div>
    </template>

    <div class="space-y-4 p-6 relative">
      <div class="flex items-center gap-2 text-[10px] font-bold text-orange-500 uppercase tracking-[0.2em]">
        <span class="w-8 h-[1px] bg-orange-200"></span>
        <span>{{ formatDate(post.date) }}</span>
      </div>
      
      <h3 class="font-black text-2xl leading-[1.1] text-slate-900 group-hover:text-orange-600 transition-colors duration-300">
        {{ post.title }}
      </h3>
      
      <p class="text-sm text-slate-600 line-clamp-2 leading-relaxed">
        {{ post.description }}
      </p>

      <div class="pt-2 flex items-center gap-2 text-orange-600 font-bold text-xs group-hover:gap-4 transition-all duration-300">
        Ler mais <UIcon name="i-heroicons-arrow-right" class="w-4 h-4" />
      </div>
    </div>
  </UCard>
</template>

<script setup>
defineProps({
  post: {
    type: Object,
    required: true
  }
})

const formatDate = (dateString) => {
  return new Date(dateString).toLocaleDateString('pt-BR', {
    day: 'numeric',
    month: 'long',
    year: 'numeric'
  })
}
</script>
