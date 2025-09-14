<template>
  <v-container class="projects-section my-12">
    <h2 class="section-title mb-8">Projetos</h2>
    <v-row dense>
      <v-col v-for="project in projects" :key="project.name" cols="12">
        <v-card class="project-card" outlined>
          <v-card-title class="project-title">
            <v-btn
              :href="project.url"
              target="_blank"
              rel="noopener"
              variant="text"
              class="project-link"
            >
              {{ project.name.toUpperCase() }}
            </v-btn>
          </v-card-title>
          <v-card-subtitle class="project-description">
            {{ project.description }}
          </v-card-subtitle>
            <v-card-text class="project-tech">
                <v-avatar
                    v-for="tech in project.techIcons"
                    :key="tech.name"
                    size="36"
                    class="me-2 tech-avatar"
                >
                    <v-img :src="tech.icon" :alt="tech.name" class="tech-img" />
                </v-avatar>
            </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
// Ícones podem ser imagens locais em /assets ou URLs externas
import nuxtIcon from '/src/assets/Nuxt.png'
import vueIcon from '/src/assets/Vue.png'
import tsIcon from '/src/assets/TypeScript.png'
import jsIcon from '/src/assets/JavaScript.png'
import cssIcon from '/src/assets/CSS3.png'
import pythonIcon from '/src/assets/Python.png'
import pytorchIcon from '/src/assets/PyTorch.png'
import htmlIcon from '/src/assets/HTML5.png'
import jqueryIcon from '/src/assets/jQuery.png'
import bootstrapIcon from '/src/assets/Bootstrap.png'
import nodeIcon from '/src/assets/Node.png'
import expressIcon from '/src/assets/Express.png'
import sqliteIcon from '/src/assets/SQLite.png'
import reactIcon from '/src/assets/React.png'
import viteIcon from '/src/assets/Vite.png'
import githubIcon from '/src/assets/GitHub.png'
import vercelIcon from '/src/assets/Vercel.png'

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
</script>

<style scoped>
.projects-section {
  padding: 50px 20px;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.05);
}

.projects-section:hover {
  box-shadow: 0 16px 30px rgba(0,0,0,0.2);
  transform: scale(1.02); 
  cursor: pointer;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 900;
  text-align: center;
  color: #e91e63;
  text-transform: uppercase;
  text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
}

.project-card {
  border-radius: 12px;
  transition: transform 0.3s, box-shadow 0.3s;
  border: 2px solid #f0f0f0;
  margin-bottom: 20px;
  cursor: pointer;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 25px rgba(233,30,99,0.4);
}

.project-title {
  font-size: 1.3rem;
  font-weight: 900;
  color: #222;
}

.project-description {
  font-size: 0.95rem;
  color: #333;
  margin-top: 4px;
}

.project-tech {
  font-size: 0.9rem;
  color: #e91e63;
  margin-top: 8px;
  display: flex;
  align-items: center;
}

.tech-avatar {
  border-radius: 8px;
  overflow: hidden;
}

.tech-img {
  object-fit: contain;
  width: 100%;
  height: 100%;
}

.project-link {
  color: #e91e63;
  text-transform: uppercase;
  font-weight: 900;
}
</style>
