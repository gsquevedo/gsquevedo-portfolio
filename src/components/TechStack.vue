<template>
  <v-container class="tech-stack" fluid>
    <h2 class="tech-title">Tecnologias</h2>
    <v-row justify="center" align="center" class="mt-4" dense>
      <v-col
        v-for="tech in technologies"
        :key="tech.name"
        cols="6"
        sm="4"
        md="2"
        class="d-flex justify-center"
      >
        <v-card class="tech-card" elevation="3">
          <v-img :src="tech.icon" class="tech-icon" contain></v-img>
          <v-card-text class="tech-name">{{ tech.name }}</v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
// Importando todas as imagens corretamente
import VueIcon from '/src/assets/Vue.png'
import NuxtIcon from '/src/assets/Nuxt.png'
import ReactIcon from '/src/assets/React.png'
import NextIcon from '/src/assets/Next.png'
import TSIcon from '/src/assets/TypeScript.png'
import JSIcon from '/src/assets/JavaScript.png'
import HTMLIcon from '/src/assets/HTML5.png'
import CSSIcon from '/src/assets/CSS3.png'
import PythonIcon from '/src/assets/Python.png'
import FastAPIIcon from '/src/assets/FastAPI.png'
import NodeIcon from '/src/assets/Node.png'
import PostgreSQLIcon from '/src/assets/PostgreSQL.png'
import SQLiteIcon from '/src/assets/SQLite.png'
import MySQLIcon from '/src/assets/MySQL.png'

// Array de tecnologias com ícones importados
const technologies = [
  { name: 'Vue.js', icon: VueIcon },
  { name: 'Nuxt.js', icon: NuxtIcon },
  { name: 'React', icon: ReactIcon },
  { name: 'Next.js', icon: NextIcon },
  { name: 'TypeScript', icon: TSIcon },
  { name: 'JavaScript', icon: JSIcon },
  { name: 'HTML5', icon: HTMLIcon },
  { name: 'CSS3', icon: CSSIcon },
  { name: 'Python', icon: PythonIcon },
  { name: 'FastAPI', icon: FastAPIIcon },
  { name: 'Node.js', icon: NodeIcon },
  { name: 'PostgreSQL', icon: PostgreSQLIcon },
  { name: 'SQLite', icon: SQLiteIcon },
  { name: 'MySQL', icon: MySQLIcon }
]
</script>

<style scoped>
.tech-stack {
  padding: 50px 20px;
  background-color: #ffffff;
  border-radius: 12px;
  margin-top: 20px;
  /* border: 3px solid #e91e63; */
  box-shadow: 0 8px 25px rgba(0,0,0,0.1);
}

.tech-stack:hover {
  box-shadow: 0 16px 30px rgba(0,0,0,0.2);
  transform: scale(1.02); 
  cursor: pointer;
}

.tech-title {
  font-size: 2.5rem;           
  font-weight: 800;              
  margin-bottom: 20px;          
  text-align: center;            
  color: #e91e63;                
  text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
  text-transform: uppercase;   
}

.tech-card {
  width: 120px;
  height: 140px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  border-radius: 12px;
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
  margin-top: 20px;
}

.tech-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(233,30,99,0.4) !important;
}


.tech-icon {
  width: 60px;
  height: 60px;
  margin-bottom: 10px;
  margin-top: 10px;
}

.tech-name {
  font-weight: 600;
  font-size: 0.95rem;
  color: #222;
}
</style>
