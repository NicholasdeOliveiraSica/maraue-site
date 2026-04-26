<template>
  <div class="space-y-24">
    <!-- History Section -->
    <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      <div class="space-y-8">
        <UBadge color="primary" variant="subtle" size="lg" class="rounded-full px-4 font-bold uppercase tracking-widest">Nossa Jornada</UBadge>
        <h1 class="text-5xl md:text-6xl font-black text-slate-900 leading-[0.9]">
          Uma História de <br/>
          <span class="text-orange-600">Resistência e Arte</span>
        </h1>
        <div class="prose prose-orange lg:prose-xl text-slate-600 leading-relaxed font-medium">
          <p>
            O Grupo de Capoeira Marauê nasceu da paixão pela preservação da cultura afro-brasileira e do desejo de fomentar o esporte e a cidadania em Bombinhas, SC. Sob a liderança de mestres dedicados, o grupo tornou-se uma referência regional, integrando tradição e modernidade.
          </p>
          <p>
            Nossa missão é educar através da arte, proporcionando saúde física e mental para nossos alunos, além de manter viva a chama da capoeira em nossa comunidade.
          </p>
        </div>
      </div>
      <div class="relative">
        <div class="absolute -inset-4 bg-orange-100 rounded-[3rem] -rotate-3 blur-2xl opacity-50"></div>
        <img src="https://images.unsplash.com/photo-1590559063737-013f98270514?q=80&w=1000&auto=format&fit=crop" alt="Capoeira Training" class="relative rounded-[2.5rem] shadow-2xl border-4 border-white object-cover aspect-square" />
      </div>
    </section>

    <!-- Timeline Section -->
    <section class="space-y-12 bg-white/40 backdrop-blur-md p-8 md:p-16 rounded-[3rem] border border-orange-100/50 shadow-xl shadow-orange-900/5">
      <div class="text-center space-y-4 max-w-2xl mx-auto">
        <h2 class="text-4xl font-black text-slate-900 tracking-tighter">Marcos Históricos</h2>
        <p class="text-slate-500 font-medium">Uma década de dedicação à cultura em Santa Catarina.</p>
      </div>
      
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
        <div v-for="milestone in milestones" :key="milestone.year" class="p-8 bg-white rounded-3xl border border-orange-50 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all duration-300 group">
          <div class="text-4xl font-black text-orange-600/20 group-hover:text-orange-600 transition-colors mb-4">{{ milestone.year }}</div>
          <h3 class="text-xl font-black text-slate-900 mb-2 leading-tight">{{ milestone.title }}</h3>
          <p class="text-sm text-slate-500 leading-relaxed font-medium">{{ milestone.description }}</p>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="space-y-12">
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-6">
        <div class="space-y-4">
          <h2 class="text-4xl font-black text-slate-900 tracking-tighter">Liderança Marauê</h2>
          <p class="text-slate-500 font-medium">Mestres e graduados que mantêm o axé do nosso grupo.</p>
        </div>
        <UButton label="Ver Todos os Membros" variant="ghost" color="primary" icon="i-heroicons-arrow-right" trailing class="font-bold" />
      </div>

      <div class="grid grid-cols-2 lg:grid-cols-4 gap-8">
        <div v-for="member in team" :key="member.name" class="relative group">
          <div class="aspect-[4/5] rounded-[2.5rem] overflow-hidden shadow-lg border border-white/50 relative">
            <img :src="member.photo" :alt="member.name" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-110" />
            <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent opacity-80"></div>
            <div class="absolute bottom-6 left-6 right-6">
              <p class="text-[10px] font-black text-orange-400 uppercase tracking-[0.2em] mb-1">{{ member.rank }}</p>
              <h3 class="text-xl font-black text-white leading-tight">{{ member.nickname }}</h3>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const milestones = [
  { year: '2015', title: 'Fundação do Grupo', description: 'Início das atividades em Bombinhas com as primeiras aulas comunitárias.' },
  { year: '2018', title: 'Primeiro Batizado', description: 'Evento marcante que graduou a primeira turma oficial de alunos.' },
  { year: '2023', title: 'Expansão Regional', description: 'Reconhecimento oficial como entidade cultural de destaque no município.' },
  { year: '2025', title: '10 Anos de Marauê', description: 'Celebração de uma década de história e resistência cultural.' }
]

const team = [
  { nickname: 'Mestre X', name: 'Mestre X', rank: 'Mestre', photo: 'https://i.pravatar.cc/150?u=mestre' },
  { nickname: 'Contramestre Y', name: 'Contramestre Y', rank: 'Contramestre', photo: 'https://i.pravatar.cc/150?u=contra' },
  { nickname: 'Professor Z', name: 'Professor Z', rank: 'Professor', photo: 'https://i.pravatar.cc/150?u=prof' },
  { nickname: 'Graduado A', name: 'Graduado A', rank: 'Graduado', photo: 'https://i.pravatar.cc/150?u=grad' }
]

useSeoMeta({
  title: 'Sobre Nós | Grupo Marauê',
  description: 'Conheça a história, os marcos e a equipe do Grupo de Capoeira Marauê.'
})
</script>
