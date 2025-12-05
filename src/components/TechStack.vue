<template>
  <v-container id="tech" class="tech-section fade-wrapper" fluid>
    <v-row justify="center">
      <v-col cols="12">
        <div class="tech-card-container fade-up">

          <div class="title-wrapper">
            <h2 class="tech-title">Tecnologias</h2>
            <div class="title-underline"></div>
          </div>

          <v-row
            justify="center"
            align="center"
            class="tech-grid"
          >
            <v-col
              v-for="(tech, index) in technologies"
              :key="tech.name"
              cols="6"     
              md="3"       
              class="tech-col"
            >
              <div
                class="icon-circle fade-up"
                :style="{ '--delay': `${index * 60}ms` }"
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
  padding: 30px 0;
}

.tech-card-container {
  max-width: 980px;
  margin: 0 auto;
}

.title-wrapper {
  text-align: center;
  margin-bottom: 40px;
}

.tech-title {
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
  from { width: 0; opacity: 0; }
  to   { width: 60px; opacity: 1; }
}

.fade-up {
  opacity: 0;
  transform: translateY(25px);
  filter: blur(5px);

  transition:
    opacity .7s ease,
    transform .7s ease,
    filter .7s ease;
}

.fade-up.visible {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

.tech-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.tech-col {
  display: flex;
  justify-content: center;
}

.icon-circle {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  background: #a7919d;

  display: flex;
  align-items: center;
  justify-content: center;

  box-shadow: 0 4px 12px rgba(0,0,0,0.12);

  transition: transform .35s cubic-bezier(.25,.46,.45,.94),
              box-shadow .25s ease;

  animation: iconPop .7s ease forwards;
  opacity: 0;
  animation-delay: var(--delay, 0ms);
}

@keyframes iconPop {
  0%   { opacity: 0; transform: scale(.6) translateY(12px); }
  60%  { opacity: 1; transform: scale(1.05) translateY(0); }
  100% { opacity: 1; transform: scale(1); }
}

.icon-circle:hover {
  transform: translateY(-6px) scale(1.05);
  box-shadow: 0 10px 24px rgba(0,0,0,0.18);
  background: #9a7f8d;
}

.tech-img {
  width: 52px;
  height: 52px;
  object-fit: contain;
}

@media (max-width: 600px) {
  .icon-circle {
    width: 75px;
    height: 75px;
  }

  .tech-img {
    width: 42px;
    height: 42px;
  }
}

@media (max-width: 360px) {
  .icon-circle {
    width: 65px;
    height: 65px;
  }

  .tech-img {
    width: 36px;
    height: 36px;
  }
}
</style>
