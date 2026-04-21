<template>
  <div>
    <section class="section-spacing" :aria-label="$t('team.title')">
      <div class="section-container">
        <PageHeader
          :title="$t('team.title')"
          :subtitle="$t('team.subtitle')"
        />

        <!-- How it formed -->
        <div class="card-base mb-12 border-l-4 border-l-gold-400">
          <p class="text-sm text-ink-700 leading-relaxed">
            {{ locale === 'es'
              ? 'Este equipo no se planificó. Se formó de manera orgánica cuando profesionales de distintos campos — tecnología, medicina, IA, investigación — vieron un caso que les interpeló y decidieron aportar lo que sabían. No hay jerarquía formal. Hay un objetivo compartido: que la biología de este tumor guíe el tratamiento.'
              : 'This team wasn\'t planned. It formed organically when professionals from different fields — technology, medicine, AI, research — saw a case that challenged them and decided to contribute what they knew. There is no formal hierarchy. There is a shared goal: let this tumor\'s biology guide treatment.'
            }}
          </p>
        </div>

        <h3 class="font-display font-semibold text-ink-800 text-sm uppercase tracking-wider mb-6">
          {{ locale === 'es' ? 'El equipo de Miriam' : 'Miriam\'s team' }}
        </h3>

        <div class="grid sm:grid-cols-2 gap-4 mb-12 stagger-children">
          <TeamCard
            v-for="member in coreTeam"
            :key="member.role"
            :member="member"
          />
        </div>

        <h3 class="font-display font-semibold text-ink-800 text-sm uppercase tracking-wider mb-6">
          {{ locale === 'es' ? 'Red médica de apoyo' : 'Medical support network' }}
        </h3>

        <div class="grid sm:grid-cols-2 gap-4 mb-12 stagger-children">
          <TeamCard
            v-for="member in medicalNetwork"
            :key="member.role"
            :member="member"
          />
        </div>

        <h3 class="font-display font-semibold text-ink-800 text-sm uppercase tracking-wider mb-6">
          {{ locale === 'es' ? 'Colaboradores' : 'Collaborators' }}
        </h3>

        <div class="grid sm:grid-cols-2 gap-4 stagger-children">
          <TeamCard
            v-for="member in collaborators"
            :key="member.role"
            :member="member"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const { locale } = useI18n()

const coreTeam = computed(() =>
  locale.value === 'es'
    ? [
        { role: 'La paciente', description: 'Ingeniera de software y divulgadora tecnológica. Investiga activamente su caso combinando oncología de precisión e inteligencia artificial. Coordina toda la iniciativa.', icon: 'ph:user-circle-fill', color: 'gold' as const },
        { role: 'Experto en IA y documentación clínica', description: 'Experto en inteligencia artificial. Genera y estructura la documentación clínica del caso con modelos de lenguaje avanzados, conectando la parte técnica con la médica.', icon: 'ph:brain-fill', color: 'ocean' as const },
        { role: 'Experta en bioinformática y decisiones clínicas', description: 'Bioingeniera con amplia experiencia en oncología. Ayuda a interpretar los datos moleculares y a definir los próximos pasos del plan diagnóstico y terapéutico.', icon: 'ph:strategy-fill', color: 'gold' as const },
        { role: 'Web y comunicación', description: 'Se encarga de la web, mantiene la información actualizada y cuida que todo sea comprensible para cualquier visitante.', icon: 'ph:code-fill', color: 'ocean' as const },
        { role: 'Estrategia y navegación sanitaria', description: 'Experiencia directa navegando el sistema sanitario español para acceder a tratamientos complejos. Aporta asesoramiento estratégico y conocimiento del contexto regulatorio.', icon: 'ph:compass-fill', color: 'ink' as const },
      ]
    : [
        { role: 'The patient', description: 'Software engineer and tech communicator. Actively researches her own case combining precision oncology and artificial intelligence. Coordinates the entire initiative.', icon: 'ph:user-circle-fill', color: 'gold' as const },
        { role: 'AI & Clinical Documentation Expert', description: 'Artificial intelligence expert. Generates and structures the clinical documentation using advanced language models, bridging the technical and medical domains.', icon: 'ph:brain-fill', color: 'ocean' as const },
        { role: 'Bioinformatics & Clinical Decision Expert', description: 'Bioengineer with extensive oncology experience. Helps interpret molecular data and define the next steps in the diagnostic and therapeutic plan.', icon: 'ph:strategy-fill', color: 'gold' as const },
        { role: 'Web & Communication', description: 'Manages the website, keeps information up to date, and ensures everything is understandable for any visitor.', icon: 'ph:code-fill', color: 'ocean' as const },
        { role: 'Strategy & Healthcare Navigation', description: 'Direct experience navigating the Spanish healthcare system to access complex treatments. Provides strategic advice and knowledge of the regulatory context.', icon: 'ph:compass-fill', color: 'ink' as const },
      ]
)

const medicalNetwork = computed(() =>
  locale.value === 'es'
    ? [
        { role: 'Oncólogo molecular (Europa)', description: 'Especialista en oncología molecular con reconocimiento internacional. Apoya la estrategia de análisis molecular, coordina con laboratorios de referencia y valida el enfoque clínico del caso.', icon: 'ph:stethoscope-fill', color: 'gold' as const },
        { role: 'Doctor en Ciencias del Deporte y oncología del ejercicio (España)', description: 'Investigador principal en oncología del ejercicio en la Fundación OncSport. Diseña y supervisa el programa de entrenamiento individualizado de Miriam, adaptado a su afectación ósea metastásica. Su objetivo: preservar la capacidad funcional y el estado general de cara a la próxima línea de tratamiento. La evidencia científica reciente demuestra que el ejercicio supervisado mejora la tolerancia a los tratamientos oncológicos — especialmente relevante en una paciente que ha tenido que suspender dos líneas por toxicidad severa.', icon: 'ph:barbell-fill', color: 'ocean' as const },
        { role: 'Especialista en oncología radioterápica (España)', description: 'Lleva el caso a comité tumoral multidisciplinar. Conexión directa con ensayos de terapia avanzada relevantes para este perfil.', icon: 'ph:atom-fill', color: 'ocean' as const },
        { role: 'Oncóloga tratante (España)', description: 'Oncóloga que sigue el caso desde el diagnóstico. Abierta a nuevos enfoques y en constante actualización con los últimos avances en oncología de precisión.', icon: 'ph:stethoscope-fill', color: 'ink' as const },
        { role: 'Oncóloga de precisión (EE.UU.)', description: 'Reconocida mundialmente como una de las 25 voces más influyentes en medicina de precisión. Directora asociada de investigación clínica en oncología de precisión, con más de 950 publicaciones científicas y responsable de llevar 8 fármacos a la aprobación de la FDA. Interesada en el caso de Miriam para su discusión en redes internacionales de oncología de precisión.', icon: 'ph:stethoscope-fill', color: 'gold' as const },
      ]
    : [
        { role: 'Molecular Oncologist (Europe)', description: 'Internationally recognized specialist in molecular oncology. Supports the molecular analysis strategy, coordinates with reference laboratories, and validates the clinical approach.', icon: 'ph:stethoscope-fill', color: 'gold' as const },
        { role: 'Doctor of Sport Sciences & Exercise Oncology (Spain)', description: 'Principal investigator in exercise oncology at Fundación OncSport. Designs and supervises Miriam\'s individualized training programme, adapted to her metastatic bone involvement. His goal: to preserve functional capacity and performance status ahead of the next line of treatment. Recent scientific evidence shows that supervised exercise improves tolerance to oncological treatments — especially relevant for a patient who has had to discontinue two treatment lines due to severe toxicity.', icon: 'ph:barbell-fill', color: 'ocean' as const },
        { role: 'Radiation Oncology Specialist (Spain)', description: 'Brings the case to the multidisciplinary tumor committee. Direct connection to advanced therapy trials relevant to this profile.', icon: 'ph:atom-fill', color: 'ocean' as const },
        { role: 'Treating Oncologist (Spain)', description: 'Treating oncologist who has followed the case since diagnosis. Open to new approaches and continuously updating her knowledge on the latest precision oncology advances.', icon: 'ph:stethoscope-fill', color: 'ink' as const },
        { role: 'Precision Oncologist (USA)', description: 'Globally recognized as one of the 25 most influential voices in precision medicine. Associate Director of Clinical Research in precision oncology, with over 950 scientific publications and responsible for bringing 8 drugs to FDA approval. Interested in Miriam\'s case for discussion in international precision oncology networks.', icon: 'ph:stethoscope-fill', color: 'gold' as const },
      ]
)

const collaborators = computed(() =>
  locale.value === 'es'
    ? [
        { role: 'Investigadora en IA biomédica', description: 'Experiencia personal en investigación oncológica. Aporta contactos en centros de referencia y hallazgos bibliográficos clave para el caso.', icon: 'ph:magnifying-glass-fill', color: 'ocean' as const },
        { role: 'Emprendedor tech con experiencia como paciente oncológico', description: 'Aporta perspectiva de paciente y años de experiencia navegando redes de investigación, asociaciones y fuentes de financiación en oncología.', icon: 'ph:handshake-fill', color: 'gold' as const },
        { role: 'Especialista en medicina computacional', description: 'Especialista en medicina computacional con experiencia en análisis de datos genómicos. Apoyo potencial en la interpretación del perfil molecular.', icon: 'ph:dna-fill', color: 'ocean' as const },
      ]
    : [
        { role: 'Biomedical AI Researcher', description: 'Personal experience in oncology research. Contributes contacts at reference centers and key bibliographic findings for the case.', icon: 'ph:magnifying-glass-fill', color: 'ocean' as const },
        { role: 'Tech Entrepreneur & Oncology Patient', description: 'Brings a patient perspective and years of experience navigating oncology research networks, patient associations, and funding sources.', icon: 'ph:handshake-fill', color: 'gold' as const },
        { role: 'Computational Medicine Specialist', description: 'Computational medicine specialist with experience in genomic data analysis. Potential support in interpreting the molecular profile.', icon: 'ph:dna-fill', color: 'ocean' as const },
      ]
)
</script>
