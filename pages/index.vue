<template>
  <div>
    <SectionHero />
    <SectionCampaign />

    <!-- Quick science preview -->
    <section class="section-spacing" :aria-label="locale === 'es' ? 'El perfil molecular' : 'The molecular profile'">
      <div class="section-container">
        <div class="flex items-center justify-between mb-8">
          <h2 class="heading-display text-2xl sm:text-3xl text-ink-950">
            {{ locale === 'es' ? 'El perfil molecular' : 'The molecular profile' }}
          </h2>
          <NuxtLink
            :to="localePath({ name: 'ciencia' })"
            class="link-underline text-sm"
          >
            {{ locale === 'es' ? 'Ver la ciencia completa →' : 'See the full science →' }}
          </NuxtLink>
        </div>
        <MolecularProfile />
      </div>
    </section>

    <!-- In the press -->
    <section class="section-spacing bg-white/50" :aria-label="locale === 'es' ? 'En los medios' : 'In the press'">
      <div class="section-container">
        <h2 class="heading-display text-2xl sm:text-3xl text-ink-950 mb-10 text-center">
          {{ locale === 'es' ? 'En los medios' : 'In the press' }}
        </h2>
        <div class="flex flex-wrap justify-center gap-8 sm:gap-12">
          <a
            v-for="article in currentArticles"
            :key="article.url"
            :href="article.url"
            target="_blank"
            rel="noopener noreferrer"
            class="group flex flex-col items-center justify-center gap-3 p-6 bg-white rounded-xl shadow-sm hover:shadow-md transition-all duration-300 min-w-[280px] max-w-[400px]"
          >
            <span class="font-display font-bold text-lg text-ink-600 group-hover:text-ink-900 transition-colors">
              {{ article.outlet }}
            </span>
            <span class="text-sm text-ink-500 text-center leading-relaxed">
              {{ article.title }}
            </span>
          </a>
        </div>
      </div>
    </section>

    <!-- Thesis callout -->
    <section class="py-20 bg-ink-950 text-white relative overflow-hidden" :aria-label="locale === 'es' ? 'Tesis central' : 'Core thesis'">
      <!-- Decorative dots -->
      <div class="absolute inset-0 opacity-5" style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); background-size: 24px 24px;" />

      <div class="relative section-container text-center">
        <span class="tag bg-gold-500/20 text-gold-300 border-gold-500/30 mb-6 inline-flex">
          {{ locale === 'es' ? 'Tesis central' : 'Core thesis' }}
        </span>
        <blockquote class="font-display text-2xl sm:text-3xl lg:text-4xl font-semibold leading-snug max-w-3xl mx-auto">
          {{ locale === 'es'
            ? 'Las guías clínicas clasifican tumores complejos como "HR+ estándar" cuando su biología exige un abordaje de precisión.'
            : 'Clinical guidelines classify complex tumors as "standard HR+" when their biology demands a precision approach.'
          }}
        </blockquote>
        <p class="mt-6 text-ink-400 max-w-xl mx-auto leading-relaxed">
          {{ locale === 'es'
            ? 'Objetivo: un ensayo N-of-1 que siente precedente para la oncología de precisión en subtipos ultra-raros.'
            : 'Goal: an N-of-1 trial that sets a precedent for precision oncology in ultra-rare subtypes.'
          }}
        </p>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const { locale } = useI18n()
const localePath = useLocalePath()

useSeoMeta({
  title: () => locale.value === 'es'
    ? 'Miriam González — Oncología de precisión para un tumor ultra-raro'
    : 'Miriam González — Precision Oncology for an Ultra-Rare Tumor',
  description: () => locale.value === 'es'
    ? 'BC-NED con amplificación FGFR1 ×13. Una paciente con cáncer de mama metastásico que usa IA y una red internacional de expertos para acceder a la oncología de precisión. Apoya la rebiopsia molecular.'
    : 'BC-NED with FGFR1 ×13 amplification. A metastatic breast cancer patient using AI and an international expert network to access precision oncology. Support the molecular rebiopsy.',
  ogTitle: () => locale.value === 'es'
    ? 'Miriam González — Oncología de precisión para un tumor ultra-raro'
    : 'Miriam González — Precision Oncology for an Ultra-Rare Tumor',
  ogDescription: () => locale.value === 'es'
    ? 'BC-NED con amplificación FGFR1 ×13. Apoya la rebiopsia molecular avanzada que puede cambiar su tratamiento.'
    : 'BC-NED with FGFR1 ×13 amplification. Support the advanced molecular rebiopsy that could change her treatment.',
  ogType: 'website',
  ogUrl: () => locale.value === 'es' ? 'https://helpmiriam.com' : 'https://helpmiriam.com/en',
  twitterCard: 'summary_large_image',
  twitterTitle: () => locale.value === 'es'
    ? 'Miriam González — Oncología de precisión para un tumor ultra-raro'
    : 'Miriam González — Precision Oncology for an Ultra-Rare Tumor',
  twitterDescription: () => locale.value === 'es'
    ? 'BC-NED con amplificación FGFR1 ×13. Apoya la rebiopsia molecular avanzada.'
    : 'BC-NED with FGFR1 ×13 amplification. Support the advanced molecular rebiopsy.',
})

const pressArticles = {
  es: [
    {
      outlet: 'El País',
      url: 'https://elpais.com/tecnologia/2026-04-23/asi-usa-una-paciente-con-cancer-metastasico-la-ia-para-entender-su-enfermedad-cual-es-el-mejor-metodo-para-hablar-de-salud-con-chatbots.html',
      title: 'Así usa una paciente con cáncer metastásico la IA para entender su enfermedad'
    },
  ],
  en: [
    {
      outlet: 'El País',
      url: 'https://english.elpais.com/technology/2026-04-25/whats-the-best-way-to-talk-about-health-with-chatbots.html?outputType=amp',
      title: "What's the best way to talk about health with chatbots"
    },
  ],
}

const currentArticles = computed(() => pressArticles[locale.value as keyof typeof pressArticles] || [])
</script>
