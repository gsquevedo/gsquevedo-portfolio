<template>
  <v-container id="projects" class="projects-section fade-wrapper" fluid>
    <v-row justify="center">
      <v-col cols="12">

        <div class="projects-wrapper fade-up">

          <div class="title-wrapper fade-up">
            <h2 class="projects-title">Projetos</h2>
            <div class="title-underline"></div>
          </div>

          <v-row class="projects-grid" justify="center">
            <v-col
              v-for="(project, index) in projects"
              :key="project.name"
              cols="12"
              md="6"
              lg="4"
              class="project-col fade-up"
              :style="`--delay: ${index * 0.12}s`"
            >
              <v-card class="project-card" elevation="0">

                <div class="project-header">
                  <h3 class="project-name">
                    <a
                      :href="project.url"
                      target="_blank"
                      rel="noopener"
                      class="project-link"
                    >
                      {{ project.name }}
                    </a>
                  </h3>
                  <p class="project-description">{{ project.description }}</p>
                </div>

                <div class="project-tech fade-up" :style="`--delay: ${index * 0.12 + 0.1}s`">
                  <v-avatar
                    v-for="tech in project.techIcons"
                    :key="tech.name"
                    size="32"
                    class="tech-avatar"
                  >
                    <v-img :src="tech.icon" :alt="tech.name" class="tech-img" />
                  </v-avatar>
                </div>

              </v-card>
            </v-col>
          </v-row>

        </div>

      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted } from 'vue'

import nuxtIcon from '../assets/nuxt.png'
import vueIcon from '../assets/vue.png'
import tsIcon from '../assets/typescript.png'
import jsIcon from '../assets/javascript.png'
import cssIcon from '../assets/css.png'
import pythonIcon from '../assets/python.png'
import pytorchIcon from '../assets/pytorch.png'
import htmlIcon from '../assets/html.png'
import jqueryIcon from '../assets/jquery.png'
import bootstrapIcon from '../assets/bootstrap.png'
import nodeIcon from '../assets/node.png'
import expressIcon from '../assets/express.png'
import sqliteIcon from '../assets/sqlite.png'
import reactIcon from '../assets/react.png'
import viteIcon from '../assets/vite.png'
import githubIcon from '../assets/github.png'
import vercelIcon from '../assets/vercel.png'

const projects = [
  {
    name: "DNA Afetivo: Kame e Kanru",
    url: "https://github.com/gsquevedo/dna-afetivo",
    description: "Projeto interativo que explora a relação entre tecnologia e cultura indígena, combinando narrativa, audiovisual e design para apresentar histórias das culturas Kame e Kanru.",
    techIcons: [
      { name: "Nuxt.js", icon: nuxtIcon },
      { name: "Vue.js", icon: vueIcon },
      { name: "TypeScript", icon: tsIcon },
      { name: "JavaScript", icon: jsIcon },
      { name: "CSS", icon: cssIcon }
    ]
  },
  {
    name: "FaceAnimator",
    url: "https://github.com/gsquevedo/FaceAnimator",
    description: "Animação de imagens estáticas com aprendizado profundo utilizando o modelo First Order Motion Model (FOMM), permitindo reproduzir movimentos de vídeos ou outras imagens.",
    techIcons: [
      { name: "Python", icon: pythonIcon },
      { name: "PyTorch", icon: pytorchIcon }
    ]
  },
  {
    name: "Portfolio",
    url: "https://github.com/gsquevedo/Portfolio",
    description: "Site estático desenvolvido para apresentação de trabalhos acadêmicos, aplicando HTML, CSS e JQuery, com foco em responsividade e organização visual.",
    techIcons: [
      { name: "HTML", icon: htmlIcon },
      { name: "CSS", icon: cssIcon },
      { name: "JQuery", icon: jqueryIcon },
      { name: "Bootstrap", icon: bootstrapIcon }
    ]
  },
  {
    name: "AuthenticationNodejs",
    url: "https://github.com/gsquevedo/AuthenticationNodejs",
    description: "API de autenticação de usuários com Node.js e SQLite, implementando funcionalidades de cadastro, login e autenticação via token JWT.",
    techIcons: [
      { name: "Node.js", icon: nodeIcon },
      { name: "Express.js", icon: expressIcon },
      { name: "SQLite", icon: sqliteIcon }
    ]
  },
  {
    name: "FormularioReactjs",
    url: "https://github.com/gsquevedo/FormularioReactjs",
    description: "Aplicação front-end para criação de formulários dinâmicos com ReactJS e TypeScript, utilizando hooks para gerenciamento de estado e validação de campos.",
    techIcons: [
      { name: "ReactJS", icon: reactIcon },
      { name: "TypeScript", icon: tsIcon },
      { name: "Vite", icon: viteIcon }
    ]
  },
  {
    name: "Vue-Api-Github",
    url: "https://github.com/gsquevedo/Vue-Api-Github",
    description: "Aplicativo web que consome a GitHub API para buscar e exibir informações de repositórios, focando em componentes reutilizáveis e na Composition API do Vue.js.",
    techIcons: [
      { name: "Vue.js", icon: vueIcon },
      { name: "JavaScript", icon: jsIcon },
      { name: "GitHub API", icon: githubIcon },
      { name: "Vercel", icon: vercelIcon }
    ]
  }
]

onMounted(() => {
  const elements = document.querySelectorAll('.fade-up, .fade-wrapper')

  const observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        }
      })
    },
    { threshold: 0.15 }
  )

  elements.forEach(el => observer.observe(el))
})
</script>

<style scoped>
.projects-section {
  padding: 30px 0;
}

.projects-wrapper {
  max-width: 1200px;
  margin: 0 auto;
}

.projects-title {
  font-size: 2rem;
  font-weight: 800;
  color: #413a44;
  text-align: center;
  margin-bottom: 6px;
}

.title-underline {
  width: 60px;
  height: 4px;
  background-color: #a7919d;
  margin: 0 auto 40px;
  border-radius: 2px;
  opacity: 0;
  animation: underlineGrow 1s ease forwards;
}

.projects-grid {
  margin-top: 20px;
}

.project-col {
  padding: 12px;
}

.project-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px 26px;
  border: 1px solid #e7e2e5;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.06);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.project-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 30px rgba(65, 58, 68, 0.18);
}

.project-name {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 8px;
}

.project-link {
  color: #413a44;
  text-decoration: none;
  transition: color 0.2s ease;
}

.project-link:hover {
  color: #a7919d;
}

.project-description {
  color: #575058;
  font-size: 0.95rem;
  line-height: 1.45rem;
  margin-bottom: 18px;
}

.project-tech {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.tech-avatar {
  background: #f4eff2;
  border-radius: 10px;
  padding: 4px;
}

.tech-img {
  object-fit: contain;
}

.fade-up {
  opacity: 0;
  transform: translateY(20px);
  filter: blur(6px);
  transition: all 0.9s ease;
  will-change: opacity, transform, filter;
  animation-delay: var(--delay, 0s);
}

.fade-up.visible {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

.fade-wrapper {
  opacity: 0;
  transform: translateY(20px);
  filter: blur(6px);
  transition: all 0.9s ease;
}

.fade-wrapper.visible {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

@keyframes underlineGrow {
  from { width: 0; opacity: 0; }
  to   { width: 60px; opacity: 1; }
}

@media (max-width: 599px) {
  .project-card {
    padding: 18px 20px;
  }

  .projects-title {
    font-size: 1.8rem;
  }
}
</style>
