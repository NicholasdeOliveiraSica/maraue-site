<template>
  <UCard class="overflow-hidden border-2 border-orange-100 shadow-md hover:shadow-xl transition-all duration-300 group cursor-pointer relative bg-orange-50/10" @click="navigateTo(`/posts/${post.slug}`)">
    <div class="absolute top-4 right-4 z-10">
      <UBadge color="orange" variant="solid" size="lg" class="shadow-sm animate-pulse">
        EVENTO
      </UBadge>
    </div>

    <template #header>
      <div class="relative overflow-hidden aspect-video">
        <img 
          :src="post.image" 
          :alt="post.title" 
          class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
        />
      </div>
    </template>

    <div class="space-y-4 p-1">
      <div class="flex items-center gap-4 text-xs font-semibold text-orange-600 uppercase tracking-wider">
        <div class="flex items-center gap-1">
          <UIcon name="i-heroicons-calendar" class="w-4 h-4" />
          <span>{{ formatDate(post.date) }}</span>
        </div>
        <div class="flex items-center gap-1" v-if="post.location">
          <UIcon name="i-heroicons-map-pin" class="w-4 h-4" />
          <span>{{ post.location }}</span>
        </div>
      </div>
      
      <h3 class="font-extrabold text-xl leading-tight group-hover:text-orange-600 transition-colors">
        {{ post.title }}
      </h3>
      
      <p class="text-sm text-gray-700 leading-relaxed">
        {{ post.description }}
      </p>
      
      <UButton label="Ver Detalhes" color="orange" variant="soft" block icon="i-heroicons-arrow-right" trailing />
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
