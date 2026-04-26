<template>
  <div class="space-y-24">
    <header class="space-y-6 text-center max-w-3xl mx-auto">
      <UBadge color="primary" variant="subtle" size="lg" class="rounded-full px-4 font-bold uppercase tracking-widest">Conecte-se</UBadge>
      <h1 class="text-5xl md:text-6xl font-black text-slate-900 leading-[0.9] tracking-tighter">
        Fale com o <br/>
        <span class="text-orange-600">Grupo Marauê</span>
      </h1>
      <p class="text-xl text-slate-500 font-medium leading-relaxed">
        Estamos prontos para tirar suas dúvidas, ouvir sugestões ou receber novos alunos.
      </p>
    </header>

    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
      <!-- Contact Cards -->
      <div class="lg:col-span-2 grid grid-cols-1 sm:grid-cols-2 gap-6">
        <UButton 
          v-for="contact in contacts" 
          :key="contact.label"
          :to="contact.to"
          target="_blank"
          variant="ghost"
          class="p-8 bg-white rounded-[2rem] border border-orange-50 shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all duration-300 flex flex-col items-center text-center gap-4 group"
        >
          <div class="w-16 h-16 rounded-2xl bg-orange-50 flex items-center justify-center group-hover:bg-orange-500 transition-colors duration-300">
            <UIcon :name="contact.icon" class="w-8 h-8 text-orange-600 group-hover:text-white transition-colors duration-300" />
          </div>
          <span class="font-black text-slate-900">{{ contact.label }}</span>
        </UButton>
      </div>

      <!-- Training Times Card -->
      <div class="p-8 bg-slate-900 rounded-[2.5rem] shadow-2xl relative overflow-hidden group">
        <div class="absolute inset-0 bg-gradient-to-br from-orange-600/20 to-transparent opacity-50"></div>
        <div class="relative space-y-6">
          <div class="w-12 h-12 rounded-xl bg-orange-500 flex items-center justify-center">
            <UIcon name="i-heroicons-clock" class="w-6 h-6 text-white" />
          </div>
          <h3 class="text-2xl font-black text-white leading-tight">Horários de Treino</h3>
          <ul class="space-y-4">
            <li class="flex flex-col gap-1">
              <span class="text-orange-400 text-xs font-black uppercase tracking-widest">Segunda e Quarta</span>
              <span class="text-slate-200 font-medium">19:30 — 21:00</span>
            </li>
            <li class="flex flex-col gap-1">
              <span class="text-orange-400 text-xs font-black uppercase tracking-widest">Sábado</span>
              <span class="text-slate-200 font-medium">16:00 (Roda Aberta)</span>
            </li>
          </ul>
          <UButton label="Como chegar" block color="white" variant="solid" size="lg" class="rounded-xl font-bold mt-4" />
        </div>
      </div>
    </div>

    <!-- Partners & Map -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-start">
      <section class="space-y-8 bg-white/40 backdrop-blur-md p-10 rounded-[2.5rem] border border-orange-100/50">
        <h2 class="text-3xl font-black text-slate-900 tracking-tighter flex items-center gap-3">
          <UIcon name="i-heroicons-heart" class="text-orange-500" />
          Parcerias de Valor
        </h2>
        <div class="grid grid-cols-2 gap-4">
          <div v-for="partner in partners" :key="partner.name" class="p-6 bg-white rounded-2xl border border-orange-50 flex items-center justify-center text-center group hover:border-orange-200 transition-all cursor-default">
            <span class="font-black text-slate-400 group-hover:text-orange-600 transition-colors duration-300 leading-tight">{{ partner.name }}</span>
          </div>
        </div>
      </section>

      <section class="space-y-8">
        <div class="w-full aspect-square md:aspect-video rounded-[2.5rem] overflow-hidden shadow-2xl border-8 border-white group relative">
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
