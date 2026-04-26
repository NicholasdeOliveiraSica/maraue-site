<template>
  <UCard 
    class="overflow-hidden border-2 border-orange-100/30 bg-orange-50/20 backdrop-blur-md shadow-lg hover:shadow-3xl hover:shadow-orange-500/10 transition-all duration-700 group cursor-pointer relative rounded-[2rem]" 
    @click="navigateTo(`/posts/${post.slug}`)"
    :ui="{ body: { padding: 'p-0' }, header: { padding: 'p-0' } }"
  >
    <div class="absolute top-6 right-6 z-10">
      <UBadge color="primary" variant="solid" size="lg" class="shadow-xl shadow-orange-500/40 font-black tracking-widest px-4 py-2 rounded-full border-2 border-white/20">
        EVENTO
      </UBadge>
    </div>

    <template #header>
      <div class="relative overflow-hidden aspect-video md:aspect-[21/9]">
        <img 
          :src="post.image" 
          :alt="post.title" 
          class="w-full h-full object-cover transition-transform duration-1000 group-hover:scale-110"
        />
        <div class="absolute inset-0 bg-gradient-to-t from-slate-900/80 via-slate-900/20 to-transparent"></div>
      </div>
    </template>

    <div class="space-y-6 p-8 relative">
      <div class="flex flex-wrap items-center gap-6 text-xs font-bold text-orange-600 uppercase tracking-widest">
        <div class="flex items-center gap-2 bg-orange-100/50 px-3 py-1.5 rounded-full">
          <UIcon name="i-heroicons-calendar" class="w-4 h-4" />
          <span>{{ formatDate(post.date) }}</span>
        </div>
        <div class="flex items-center gap-2 bg-orange-100/50 px-3 py-1.5 rounded-full" v-if="post.location">
          <UIcon name="i-heroicons-map-pin" class="w-4 h-4" />
          <span>{{ post.location }}</span>
        </div>
      </div>
      
      <h3 class="font-black text-3xl md:text-4xl leading-tight text-slate-900 group-hover:text-orange-600 transition-colors duration-300">
        {{ post.title }}
      </h3>
      
      <p class="text-base text-slate-600 leading-relaxed max-w-3xl">
        {{ post.description }}
      </p>
      
      <div class="pt-2">
        <UButton 
          label="Ver Detalhes do Evento" 
          color="primary" 
          variant="solid" 
          size="xl" 
          class="rounded-full px-8 font-bold shadow-lg shadow-orange-500/20 group-hover:px-10 transition-all duration-300"
          icon="i-heroicons-arrow-right" 
          trailing 
        />
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
