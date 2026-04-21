<template>
  <div>
    <section class="section-spacing" :aria-label="$t('story.title')">
      <div class="section-container">
        <PageHeader
          :title="$t('story.title')"
          :subtitle="$t('story.subtitle')"
        />

        <!-- Placeholder until the friend writes the content -->
        <article class="prose prose-ink max-w-2xl">
          <div class="card-base border-l-4 border-l-gold-400 mb-10">
            <p class="text-sm text-ink-600 italic leading-relaxed">
              {{ locale === 'es'
                ? 'Esta sección está siendo escrita por una persona cercana a Miriam. Contará su historia desde antes del diagnóstico: quién es más allá del cáncer, cómo llegó hasta aquí, y por qué importa lo que está haciendo. Estará disponible pronto.'
                : 'This section is being written by someone close to Miriam. It will tell her story from before the diagnosis: who she is beyond cancer, how she got here, and why what she\'s doing matters. Coming soon.'
              }}
            </p>
          </div>

          <!-- Story content -->
          <div class="space-y-6 text-ink-700">
            <p>
              {{ locale === 'es'
                ? 'Hace tres años, Míriam se dedicaba a tiempo completo a programar y crear contenido sobre tecnología. Entonces llegó el diagnóstico que lo cambió todo.'
                : 'Three years ago, Miriam was working full-time as a software engineer and tech content creator. Then came the diagnosis that changed everything.'
              }}
            </p>
            <p>
              {{ locale === 'es'
                ? 'Todo empezó con un dolor de espalda, sesiones de fisioterapia y médicos de cabecera que no buscaban lo que había detrás. Hasta que Míriam lo pidió ella misma.'
                : 'It started with back pain, physiotherapy sessions, and GPs who weren\'t looking for what was behind it. Until Miriam asked for it herself.'
              }}
            </p>
            <p>
              {{ locale === 'es'
                ? 'Durante dos años, Míriam ha ido reconstruyendo su vida pieza por pieza con tratamientos que han tenido que suspenderse, con un equipo que se fue formando y con una voluntad que no se ha roto.'
                : 'For two years, Miriam has been rebuilding her life piece by piece with treatments that have had to be discontinued, with a team that kept growing and with a will that has never broken.'
              }}
            </p>
            <p>
              {{ locale === 'es'
                ? 'En esta historia queremos contarte el caso de Míriam, su proceso y su rutina para que conozcas quién es más allá del diagnóstico.'
                : 'In this story, we want to tell you about Miriam\'s case, her process and her daily routine — so you can get to know who she is beyond the diagnosis.'
              }}
            </p>
          </div>
        </article>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const { locale } = useI18n()
</script>
