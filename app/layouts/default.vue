<template>
  <div class="min-h-screen bg-mesh text-slate-900 font-sans flex flex-col md:flex-row overflow-x-hidden">
    <!-- Desktop Sidebar -->
    <aside class="hidden md:flex w-72 border-r border-orange-100/50 flex-col sticky top-0 h-screen p-8 bg-white/50 backdrop-blur-xl z-50">
      <div class="mb-12 px-2">
        <NuxtLink to="/" class="flex items-center gap-3 group">
          <div class="relative">
            <div class="absolute -inset-1 bg-orange-500 rounded-full blur opacity-25 group-hover:opacity-50 transition duration-300"></div>
            <img src="https://marauecapoeira.com.br/wp-content/uploads/2023/06/m4-1.jpg" alt="Marauê Logo" class="relative w-12 h-12 rounded-full object-cover border-2 border-white shadow-sm" />
          </div>
          <span class="text-2xl font-black tracking-tighter text-slate-900 group-hover:text-orange-600 transition-colors">Marauê</span>
        </NuxtLink>
      </div>
      
      <nav class="flex-1 space-y-3">
        <NuxtLink 
          v-for="link in navigation" 
          :key="link.to" 
          :to="link.to"
          class="flex items-center gap-4 px-5 py-3.5 rounded-2xl transition-all duration-300 group relative overflow-hidden"
          :class="[route.path === link.to ? 'bg-orange-500 text-white font-bold shadow-lg shadow-orange-200' : 'hover:bg-orange-50 text-slate-600 hover:text-orange-600']"
        >
          <UIcon :name="link.icon" class="w-6 h-6 transition-transform duration-300 group-hover:scale-110 z-10" />
          <span class="z-10">{{ link.label }}</span>
          
          <!-- Hover background effect for non-active links -->
          <div v-if="route.path !== link.to" class="absolute inset-0 bg-orange-100/50 translate-x-[-100%] group-hover:translate-x-0 transition-transform duration-300"></div>
        </NuxtLink>
      </nav>

      <footer class="mt-auto pt-8 border-t border-orange-100/50 text-xs text-slate-400">
        <p class="font-medium">© {{ new Date().getFullYear() }} Grupo Marauê</p>
        <p class="mt-1 opacity-75">Bombinhas - SC</p>
      </footer>
    </aside>

    <!-- Mobile Header -->
    <header class="md:hidden sticky top-0 bg-white/80 backdrop-blur-md border-b border-orange-100/50 z-50 px-6 h-18 flex items-center justify-between">
      <NuxtLink to="/" class="flex items-center gap-3">
        <img src="https://marauecapoeira.com.br/wp-content/uploads/2023/06/m4-1.jpg" alt="Marauê Logo" class="w-10 h-10 rounded-full object-cover border-2 border-orange-500/20" />
        <span class="text-xl font-black tracking-tighter text-slate-900">Marauê</span>
      </NuxtLink>

      <UDropdownMenu :items="mobileItems" :content="{ align: 'end' }">
        <UButton color="primary" variant="ghost" icon="i-heroicons-bars-3-bottom-right" size="xl" class="rounded-full" />
      </UDropdownMenu>
    </header>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <div class="max-w-5xl mx-auto px-6 py-10 md:py-16">
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


