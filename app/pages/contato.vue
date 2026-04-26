<template>
  <div class="space-y-16">
    <header class="space-y-4">
      <h1 class="text-4xl font-bold text-gray-900 border-b-4 border-orange-500 pb-2 inline-block">Contato & Localização</h1>
      <p class="text-lg text-gray-600">
        Entre em contato conosco, conheça nossos parceiros ou venha nos visitar em Bombinhas.
      </p>
    </header>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
      <!-- Contact Info -->
      <section class="space-y-8">
        <h2 class="text-2xl font-bold text-gray-800 flex items-center gap-2">
          <UIcon name="i-heroicons-chat-bubble-left-right" class="text-orange-500" />
          Fale Conosco
        </h2>
        
        <div class="space-y-4">
          <UButton 
            v-for="contact in contacts" 
            :key="contact.label"
            :icon="contact.icon"
            :label="contact.label"
            :to="contact.to"
            target="_blank"
            color="orange"
            variant="soft"
            size="xl"
            block
            class="justify-start py-4"
          />
        </div>

        <div class="p-6 bg-orange-50 rounded-2xl border border-orange-100">
          <h3 class="font-bold text-orange-900 mb-2">Horários de Treino</h3>
          <ul class="text-sm text-orange-800 space-y-1">
            <li>Segunda e Quarta: 19:30 - 21:00</li>
            <li>Sábado (Roda Aberta): 16:00</li>
          </ul>
        </div>
      </section>

      <!-- Partners -->
      <section class="space-y-8">
        <h2 class="text-2xl font-bold text-gray-800 flex items-center gap-2">
          <UIcon name="i-heroicons-heart" class="text-orange-500" />
          Nossos Parceiros
        </h2>
        
        <div class="grid grid-cols-2 gap-4">
          <div v-for="partner in partners" :key="partner.name" class="p-4 bg-white border border-gray-100 rounded-xl flex items-center justify-center grayscale hover:grayscale-0 transition-all cursor-default">
            <span class="font-bold text-gray-400 group-hover:text-orange-500">{{ partner.name }}</span>
          </div>
        </div>
      </section>
    </div>

    <!-- Map Section -->
    <section class="space-y-6">
      <h2 class="text-2xl font-bold text-gray-800 flex items-center gap-2">
        <UIcon name="i-heroicons-map-pin" class="text-orange-500" />
        Onde Treinamos
      </h2>
      <div class="w-full aspect-video md:aspect-[21/9] rounded-3xl overflow-hidden shadow-lg border-4 border-white">
        <iframe 
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d14197.3563914856!2d-48.5134707!3d-27.1402287!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94d89617514a600d%3A0x600b3d6859846b0!2sBombinhas%2C%20SC!5e0!3m2!1spt-BR!2sbr!4v1713123456789!5m2!1spt-BR!2sbr" 
          width="100%" 
          height="100%" 
          style="border:0;" 
          allowfullscreen="" 
          loading="lazy" 
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
      </div>
    </section>
  </div>
</template>

<script setup>
const contacts = [
  { label: 'Instagram @marauecapoeira', to: 'https://instagram.com/marauecapoeira', icon: 'i-simple-icons-instagram' },
  { label: 'WhatsApp (47) 99999-9999', to: 'https://wa.me/5547999999999', icon: 'i-simple-icons-whatsapp' },
  { label: 'Facebook Marauê', to: 'https://facebook.com/marauecapoeira', icon: 'i-simple-icons-facebook' },
  { label: 'Email contato@maraue.com.br', to: 'mailto:contato@maraue.com.br', icon: 'i-heroicons-envelope' }
]

const partners = [
  { name: 'Prefeitura de Bombinhas' },
  { name: 'Fundação de Cultura' },
  { name: 'Academia Corpo Ativo' },
  { name: 'Surf Shop Maramar' }
]

useSeoMeta({
  title: 'Contato | Grupo Marauê',
  description: 'Fale com o Grupo Marauê, conheça nossos parceiros e localize nossos treinos em Bombinhas - SC.'
})
</script>
