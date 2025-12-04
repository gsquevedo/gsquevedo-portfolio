<template>
  <v-container id="tech" class="tech-section fade-wrapper" fluid>
    <v-row justify="center">
      <v-col cols="12">

        <div class="tech-card-container fade-up">

          <div class="title-wrapper">
            <h2 class="tech-title">Tecnologias</h2>
            <div class="title-underline"></div>
          </div>

          <v-row justify="center" align="center" class="tech-grid">

            <v-col
              v-for="(tech, index) in technologies"
              :key="tech.name"
              cols="4"
              sm="3"
              md="2"
              class="tech-col"
            >
              <div
                class="icon-circle fade-up"
                :style="{ '--delay': `${index * 80}ms` }"
              >
                <v-tooltip location="top">
                  <template #activator="{ props }">
                    <img
                      v-bind="props"
                      :src="tech.img"
                      :alt="tech.name"
                      class="tech-img"
                    />
                  </template>
                  <span>{{ tech.name }}</span>
                </v-tooltip>
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
import vue from '../assets/vue.png'
import react from '../assets/react.png'
import nuxt from '../assets/nuxt.png'
import next from '../assets/next.png'
import typescript from '../assets/typescript.png'
import javascript from '../assets/javascript.png'
import html from '../assets/html.png'
import css from '../assets/css.png'
import python from '../assets/python.png'
import pytorch from '../assets/pytorch.png'
import fastapi from '../assets/fastapi.png'
import node from '../assets/node.png'
import express from '../assets/express.png'
import github from '../assets/github.png'
import postgres from '../assets/postgres.png'
import sqlite from '../assets/sqlite.png'
import mysql from '../assets/mysql.png'

const technologies = [
  { name: "Vue.js", img: vue },
  { name: "React", img: react },
  { name: "Nuxt.js", img: nuxt },
  { name: "Next.js", img: next },
  { name: "TypeScript", img: typescript },
  { name: "JavaScript", img: javascript },
  { name: "HTML5", img: html },
  { name: "CSS3", img: css },
  { name: "Python", img: python },
  { name: "PyTorch", img: pytorch },
  { name: "FastAPI", img: fastapi },
  { name: "Node.js", img: node },
  { name: "Express.js", img: express },
  { name: "GitHub", img: github },
  { name: "PostgreSQL", img: postgres },
  { name: "SQLite", img: sqlite },
  { name: "MySQL", img: mysql },
]

// animação de entrada
onMounted(() => {
  const section = document.querySelector("#tech")

  const reveal = () => {
    if (window.scrollY + window.innerHeight >= section.offsetTop + 100) {
      const items = section.querySelectorAll(".fade-up")
      items.forEach(item => item.classList.add("visible"))
      window.removeEventListener("scroll", reveal)
    }
  }

  window.addEventListener("scroll", reveal)
  reveal()
})
</script>

<style scoped>
.tech-section {
  padding: 60px 30px;
  background-color: #ffffff;
  border-radius: 12px;
  margin-top: 15px;
  box-shadow: 0 8px 30px rgba(0,0,0,0.12);

  /* sutil parallax ao rolar */
  transform: translateY(0);
  transition: transform 0.4s ease;
}

.tech-title {
  font-size: 2.4rem;
  font-weight: 800;
  color: #413a44;
  text-align: center;
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
  from { width: 0; opacity: 0; }
  to   { width: 60px; opacity: 1; }
}

.fade-up {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeUpAnim 0.9s ease forwards;
  animation-delay: var(--delay, 0ms);
}

@keyframes fadeUpAnim {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.tech-grid {
  margin-top: 30px;
}

.tech-img {
  width: 55%;
  height: 55%;
  object-fit: contain;
}

.icon-circle {
  width: 95px;
  height: 95px;
  border-radius: 50%;
  background-color: #a7919d;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.25s ease;
  cursor: pointer;
}

.icon-circle:hover {
  transform: scale(1.07);
}

.tech-icon {
  font-size: 42px !important;
  color: #ffffff !important;
}

@media (max-width: 959px) {
  .tech-card-container {
    padding: 40px 20px;
    margin-top: -20px;
  }

  .tech-title {
    font-size: 2rem;
  }

  .icon-circle {
    width: 80px;
    height: 80px;
  }

  .tech-icon {
    font-size: 36px !important;
  }
}

@media (max-width: 599px) {
  .icon-circle {
    width: 70px;
    height: 70px;
  }

  .tech-icon {
    font-size: 32px !important;
  }
}

</style>
