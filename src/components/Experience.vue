<template>
  <v-container class="experience-section my-12">
    <h2 class="experience-title mb-8">Experiência Profissional</h2>
    <v-row dense>
      <v-col v-for="exp in experiences" :key="exp.company" cols="12" md="6">
        <v-card class="experience-card" outlined>
          <v-card-title class="experience-role">
            {{ exp.role }}
          </v-card-title>
          <v-card-subtitle class="experience-company">
            {{ exp.company }}
          </v-card-subtitle>
          <v-card-text class="experience-text">
            <p class="experience-period">{{ exp.period }}</p>
            <ul>
              <li v-for="desc in exp.details" :key="desc">{{ desc }}</li>
            </ul>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
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
];
</script>


<style scoped>
.experience-section {
  padding: 50px 20px;
  /* border: 4px solid #e91e63; */
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.05);
}

.experience-section:hover {
  box-shadow: 0 16px 30px rgba(0,0,0,0.2);
  transform: scale(1.02); 
  cursor: pointer;
}

.experience-title {
  font-size: 2.5rem;
  font-weight: 800;
  text-align: center;
  color: #e91e63;
  text-transform: uppercase;
  text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
}

.experience-card {
  border-radius: 12px;
  transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
  border: 2px solid #f0f0f0;
  margin-bottom: 20px;
  cursor: pointer;
}

.experience-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 25px rgba(233, 30, 99, 0.4) !important; /* sombra rosa */
}

.experience-role {
  font-size: 1.2rem;
  font-weight: 700;
  color: #222;
}

.experience-company {
  font-size: 1rem;
  font-weight: 500;
  color: #555;
  margin-bottom: 8px;
}

.experience-text {
  font-size: 0.95rem;
  color: #333;
}

.experience-period {
  font-weight: 600;
  margin-bottom: 6px;
  color: #e91e63;
}

ul {
  padding-left: 20px;
  margin: 0;
}

li {
  margin-bottom: 6px;
}
</style>
