<template>
  <v-container
    id="about"
    class="about-me"
    fluid
  >
    <v-row align="center" justify="center">
      <v-col cols="12" md="8" class="about-text">

        <div class="title-wrapper fade-item">
          <h2 class="about-title">Sobre Mim</h2>
          <div class="title-underline"></div>
        </div>

        <p class="about-description fade-item" style="--delay: 0.1s;">
          Sou <strong>Gabriele Quevedo</strong>, desenvolvedora com mais de <strong>3 anos de experiência em Frontend</strong>,
          criando interfaces modernas, responsivas e centradas na experiência do usuário com
          <strong>Vue.js</strong> e <strong>React</strong>. Minha atuação é guiada por código limpo, boas práticas
          e atenção aos detalhes visuais e funcionais.
        </p>

        <p class="about-description fade-item" style="--delay: 0.25s;">
          Nos últimos anos, ampliei minha trajetória para o <strong>Backend</strong>, trabalhando com
          <strong>Python/Django</strong> no desenvolvimento de APIs estruturadas, escaláveis e seguras.
          Essa evolução tem fortalecido minha visão full stack, permitindo integrar Frontend e Backend
          de forma eficiente e consistente.
        </p>

        <p class="about-description fade-item" style="--delay: 0.4s;">
          Também tive a oportunidade de atuar diretamente com <strong>Inteligência Artificial</strong> por meio de
          uma <strong>bolsa acadêmica</strong>, onde trabalhei com análise de dados, automação e modelos em Python.
          Essa experiência foi essencial para o desenvolvimento do meu <strong>TCC</strong>, que explora o uso de
          <strong>Agentes LLM</strong> para priorização de requisitos de software — unindo engenharia de software,
          IA generativa e automação inteligente.
        </p>

        <p class="about-description fade-item" style="--delay: 0.55s;">
          Sou movida por desafios, curiosidade e pela vontade de criar soluções que realmente funcionam.
          Atualmente, busco minha primeira oportunidade como <strong>Desenvolvedora Júnior</strong> para aplicar meus
          conhecimentos, continuar evoluindo e contribuir com produtos que geram valor real para negócios e pessoas.
        </p>

      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted } from "vue"

onMounted(() => {
  const items = document.querySelectorAll(".fade-item")

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible")
        }
      })
    },
    {
      threshold: 0.2,
    }
  )

  items.forEach(item => observer.observe(item))
})
</script>

<style scoped>
.about-me {
  padding: 40px 30px;
  margin-top: -40px;
  transform: translateY(0);
  transition: transform 0.4s ease;
}

.about-me:hover {
  transform: translateY(-3px);
}

.title-wrapper {
  text-align: center;
  margin-bottom: 20px;
  position: relative;
}

.about-title {
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
  animation: underlineGrow 1s ease forwards;
  opacity: 0;
}

@keyframes underlineGrow {
  0% { width: 0; opacity: 0; }
  100% { width: 60px; opacity: 1; }
}

.fade-item {
  opacity: 0;
  transform: translateY(25px);
  transition: opacity 0.8s ease, transform 0.8s ease;
  transition-delay: var(--delay, 0s);
}

.fade-item.visible {
  opacity: 1;
  transform: translateY(0);
}

.about-description {
  font-size: 1.15rem;
  line-height: 1.75;
  color: #444;
  margin-bottom: 20px;
  text-align: justify;
}

@media (max-width: 959px) {
  .about-me {
    padding: 40px 20px;
    margin-top: -20px;
  }

  .about-title {
    font-size: 2rem;
  }

  .about-description {
    font-size: 1.05rem;
  }
}
</style>
