<template>
  <!-- Barra superior -->
  <v-app-bar flat class="appbar" elevate-on-scroll>
    <v-container>
      <v-row align="center" justify="space-between" no-gutters>
        <v-col cols="auto" class="d-flex align-center">
          <!-- Logo ou título -->
          <v-img src="@/assets/logo.png" alt="Logo" max-width="150" />
        </v-col>

        <v-col cols="auto" class="d-flex align-center">
          <div class="links">
            <v-btn
              v-for="link in links"
              :key="link.href"
              :href="link.href"
              target="_blank"
              rel="noopener"
              variant="text"
              class="link-btn"
            >
              {{ link.label }}
            </v-btn>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-app-bar>

  <!-- Hero -->
  <v-container class="hero" fluid>
    <v-row align="center" justify="space-between">
      <!-- Foto do lado esquerdo -->
      <v-col cols="12" md="4" class="text-center">
        <v-avatar size="300" class="hero-avatar">
          <v-img :src="profileImg" alt="Foto de Gabriele Quevedo" />
        </v-avatar>
      </v-col>

      <!-- Texto do lado direito -->
      <v-col cols="12" md="6" class="text-left hero-text">
        <h1 class="hero-title">{{ name }}</h1>
        <p class="hero-role">{{ title }}</p>
        <p class="hero-subtitle">{{ subtitle }}</p>
        <p class="hero-info"><v-icon left>mdi-email</v-icon> gsquevedo@inf.ufsm.br</p>
        <p class="hero-info"><v-icon left>mdi-phone</v-icon> (55) 99727-6535</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import profileImg from '../assets/profile.jpeg'

const name = "Gabriele Quevedo"
const title = "Desenvolvedora Frontend"
const subtitle = "Graduanda em Ciência da Computação na UFSM"

const links = [
  { label: "GitHub", href: "https://github.com/gsquevedo" },
  { label: "LinkedIn", href: "https://www.linkedin.com/in/gsquevedo/" },
  { label: "Medium", href: "https://medium.com/@gabrielequevedo" }
]
</script>

<style scoped>
/* --- Appbar --- */
.appbar {
  background: linear-gradient(135deg, #f06292 0%, #e91e63 50%, #d81b60 100%) !important;
  color: #fff;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}



/* Links na barra */
.link-btn {
  color: #fff !important;
  text-transform: none;
  font-weight: 500;
  font-size: 0.9rem;
}

/* --- Hero --- */
.hero {
  min-height: 70vh;
  display: flex;
  align-items: center;
  background: linear-gradient(135deg, #e91e63 0%, #050505 50%, #e91e63 100%);
  color: #fff;
  padding: 60px 30px;
  /* border-radius: 12px; */
}

.hero-text {
  padding-left: 40px;
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 12px;
}

.hero-role {
  font-size: 1.2rem;
  font-style: italic;
  color: #f0f0f0;
  margin-bottom: 6px;
}

.hero-subtitle {
  font-size: 1.1rem;
  color: #e0e0e0;
  margin-bottom: 12px;
}

.hero-info {
  font-size: 1rem;
  color: #f5f5f5;
  margin-bottom: 4px;
}

/* Foto grande no lado esquerdo */
.hero-avatar {
  border: 4px solid #fff;
  box-shadow: 0 8px 30px rgba(0,0,0,0.25);
}

/* Responsivo */
@media (max-width: 768px) {
  .hero {
    text-align: center;
    border-radius: 0;
  }
  .hero-text {
    padding-left: 0;
    margin-top: 20px;
  }
}
</style>
