<template>
  <UCard class="overflow-hidden border-none shadow-sm hover:shadow-md transition-shadow duration-300 group cursor-pointer" @click="navigateTo(`/posts/${post.slug}`)">
    <template #header>
      <div class="relative overflow-hidden aspect-[4/5]">
        <img 
          :src="post.image" 
          :alt="post.title" 
          class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
        />
      </div>
    </template>

    <div class="space-y-3 p-1">
      <div class="flex items-center justify-between text-xs text-gray-500">
        <span>{{ formatDate(post.date) }}</span>
      </div>
      
      <h3 class="font-bold text-lg leading-tight group-hover:text-orange-600 transition-colors">
        {{ post.title }}
      </h3>
      
      <p class="text-sm text-gray-600 line-clamp-2">
        {{ post.description }}
      </p>
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
