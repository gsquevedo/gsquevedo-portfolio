<template>
  <v-container id="experience" class="experience-section fade-wrapper" fluid>
    <v-row justify="center">
      <v-col cols="12" md="10" lg="8">

        <div class="experience-card-container fade-up">

          <div class="title-wrapper fade-up">
            <h2 class="experience-title">Experiência Profissional</h2>
            <div class="title-underline"></div>
          </div>

          <v-row class="experience-grid" dense>
            <v-col
              v-for="(exp, index) in experiences"
              :key="exp.company"
              cols="12"
              class="exp-item-col fade-up"
              :style="`--delay: ${index * 0.12}s`"
            >
              <div class="exp-card">

                <h3 class="exp-role">{{ exp.role }}</h3>
                <p class="exp-company">{{ exp.company }}</p>
                <p class="exp-period">{{ exp.period }}</p>

                <ul class="exp-list">
                  <li v-for="desc in exp.details" :key="desc">{{ desc }}</li>
                </ul>

              </div>
            </v-col>
          </v-row>

        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted } from "vue"

const experiences = [
  {
    company: "iTec/FURG",
    role: "Desenvolvedora Frontend",
    period: "Fev 2025 – Atual",
    details: [
      "Desenvolvimento de interfaces intuitivas e responsivas com Next.js, Radix UI e shadcn/ui"
    ]
  },
  {
    company: "Freelancer",
    role: "Desenvolvedora Frontend",
    period: "Out 2024 – Jun 2025",
    details: [
      "Frontend de plataforma web para contabilização de containers",
      "Aplicação inovadora com dados geoespaciais"
    ]
  },
  {
    company: "LabInter - UFSM",
    role: "Bolsista TI",
    period: "Mai 2024 – Dez 2024",
    details: [
      "Plataforma web para projeto DNA Afetivo",
      "Aplicação de técnicas de visão computacional para animação"
    ]
  },
  {
    company: "Quasar Space",
    role: "Desenvolvedora Frontend",
    period: "Mai 2023 – Abr 2024",
    details: [
      "Desenvolvimento de mapas interativos com Deck.gl",
      "Otimização da interface frontend e visualização de dados geoespaciais"
    ]
  }
]

onMounted(() => {
  const elements = document.querySelectorAll(".fade-up, .fade-wrapper")

  const observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible")
        }
      })
    },
    { threshold: 0.15 }
  )

  elements.forEach(el => observer.observe(el))
})
</script>

<style scoped>
.experience-section {
  padding: 30px 0px;
}

.experience-card-container {
  max-width: 900px;
  margin: 0 auto;
}

.title-wrapper {
  text-align: center;
  margin-bottom: 20px;
}

.experience-title {
  font-size: 2rem;
  font-weight: 800;
  color: #413a44;
}

.title-underline {
  width: 60px;
  height: 4px;
  background-color: #a7919d;
  margin: 10px auto 0;
  border-radius: 2px;
  opacity: 0;
  animation: underlineGrow 1s ease forwards;
}

@keyframes underlineGrow {
  0% { width: 0; opacity: 0; }
  100% { width: 60px; opacity: 1; }
}

.fade-up {
  opacity: 0;
  transform: translateY(20px);
  filter: blur(6px);
  transition: all 0.9s ease;
  animation-delay: var(--delay, 0s);
}

.fade-wrapper {
  opacity: 0;
  transform: translateY(20px);
  filter: blur(6px);
  transition: all 0.9s ease;
}

.fade-up.visible,
.fade-wrapper.visible {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

.exp-role {
  font-size: 1.25rem;
  font-weight: 700;
  color: #413a44;
  margin-bottom: 4px;
}

.exp-company {
  font-weight: 600;
  color: #6e6475;
}

.exp-period {
  margin-top: 6px;
  font-weight: 600;
  color: #a7919d;
  margin-bottom: 10px;
}

.exp-list {
  padding-left: 20px;
  margin: 0;
}

.exp-list li {
  margin-bottom: 6px;
  color: #444;
  font-size: 0.98rem;
}

@media (max-width: 959px) {
  .experience-section {
    padding: 40px 20px;
  }

  .experience-title {
    font-size: 2rem;
  }
}
</style>
