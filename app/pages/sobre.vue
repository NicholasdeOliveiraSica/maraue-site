<template>
  <div class="space-y-16">
    <!-- History Section -->
    <section class="space-y-6">
      <h1 class="text-4xl font-bold text-gray-900 border-b-4 border-orange-500 pb-2 inline-block">Nossa História</h1>
      <div class="prose prose-orange lg:prose-xl text-gray-700 leading-relaxed">
        <p>
          O Grupo de Capoeira Marauê nasceu da paixão pela preservação da cultura afro-brasileira e do desejo de fomentar o esporte e a cidadania em Bombinhas, SC. Sob a liderança de mestres dedicados, o grupo tornou-se uma referência regional, integrando tradição e modernidade.
        </p>
        <p>
          Nossa missão é educar através da arte, proporcionando saúde física e mental para nossos alunos, além de manter viva a chama da capoeira em nossa comunidade.
        </p>
      </div>
    </section>

    <!-- Timeline Section -->
    <section class="space-y-8">
      <h2 class="text-3xl font-bold text-gray-900">Marcos Históricos</h2>
      <div class="space-y-8 border-l-2 border-orange-200 ml-4 pl-8 relative">
        <div v-for="milestone in milestones" :key="milestone.year" class="relative">
          <div class="absolute -left-[41px] top-1 w-4 h-4 rounded-full bg-orange-500 border-4 border-white shadow-sm"></div>
          <span class="text-orange-600 font-bold text-xl">{{ milestone.year }}</span>
          <h3 class="text-xl font-semibold text-gray-800">{{ milestone.title }}</h3>
          <p class="text-gray-600">{{ milestone.description }}</p>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="space-y-8">
      <h2 class="text-3xl font-bold text-gray-900">Membros e Graduados</h2>
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-6">
        <div v-for="member in team" :key="member.name" class="text-center group">
          <div class="relative mb-3 inline-block">
            <div class="absolute inset-0 bg-orange-500 rounded-full scale-0 group-hover:scale-105 transition-transform duration-300 opacity-20"></div>
            <img :src="member.photo" :alt="member.name" class="w-24 h-24 md:w-32 md:h-32 rounded-full object-cover border-2 border-white shadow-md relative z-10" />
          </div>
          <h3 class="font-bold text-gray-900 group-hover:text-orange-600 transition-colors">{{ member.nickname }}</h3>
          <p class="text-xs text-orange-600 font-semibold uppercase tracking-wider">{{ member.rank }}</p>
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
