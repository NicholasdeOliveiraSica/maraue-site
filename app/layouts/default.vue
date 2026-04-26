<template>
  <div class="min-h-screen bg-white text-gray-900 font-sans flex flex-col md:flex-row">
    <!-- Desktop Sidebar -->
    <aside class="hidden md:flex w-64 border-r border-gray-200 flex-col sticky top-0 h-screen p-6 bg-white z-50">
      <div class="mb-10 px-2">
        <NuxtLink to="/" class="flex items-center gap-2">
          <img src="https://marauecapoeira.com.br/wp-content/uploads/2023/06/m4-1.jpg" alt="Marauê Logo" class="w-10 h-10 rounded-full object-cover border border-orange-500 shadow-sm" />
          <span class="text-2xl font-bold tracking-tight text-orange-600">Marauê</span>
        </NuxtLink>
      </div>
      
      <nav class="flex-1 space-y-2">
        <NuxtLink 
          v-for="link in navigation" 
          :key="link.to" 
          :to="link.to"
          class="flex items-center gap-3 px-4 py-3 rounded-xl transition-all duration-200 group"
          :class="[route.path === link.to ? 'bg-orange-50 text-orange-600 font-semibold shadow-sm' : 'hover:bg-gray-50 text-gray-700 hover:text-orange-600']"
        >
          <UIcon :name="link.icon" class="w-6 h-6 transition-transform duration-200 group-hover:scale-110" />
          <span>{{ link.label }}</span>
        </NuxtLink>
      </nav>

      <footer class="mt-auto pt-6 border-t border-gray-100 text-xs text-gray-400">
        <p>© {{ new Date().getFullYear() }} Grupo Marauê</p>
        <p class="mt-1">Bombinhas - SC</p>
      </footer>
    </aside>

    <!-- Mobile Header -->
    <header class="md:hidden sticky top-0 bg-white/80 backdrop-blur-md border-b border-gray-100 z-50 px-4 h-16 flex items-center justify-between">
      <NuxtLink to="/" class="flex items-center gap-2">
        <img src="https://marauecapoeira.com.br/wp-content/uploads/2023/06/m4-1.jpg" alt="Marauê Logo" class="w-8 h-8 rounded-full object-cover border border-orange-500 shadow-sm" />
        <span class="text-xl font-bold tracking-tight text-orange-600">Marauê</span>
      </NuxtLink>

      <UDropdown :items="mobileItems" :popper="{ placement: 'bottom-end' }">
        <UButton color="orange" variant="ghost" icon="i-heroicons-bars-3-bottom-right" size="xl" />
      </UDropdown>
    </header>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <div class="max-w-4xl mx-auto px-4 py-8 md:py-12">
        <slot />
      </div>
    </main>
  </div>
</template>

<script setup>
const route = useRoute()

const navigation = [
  { label: 'Início', to: '/', icon: 'i-heroicons-home' },
  { label: 'Sobre', to: '/sobre', icon: 'i-heroicons-user-group' },
  { label: 'Contato', to: '/contato', icon: 'i-heroicons-envelope' }
]

const mobileItems = [
  navigation.map(link => ({
    label: link.label,
    icon: link.icon,
    to: link.to
  }))
]
</script>

<style>
body {
  @apply bg-gray-50;
}
</style>
