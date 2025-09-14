<template>
  <div class="contact-section">
    <v-container>
      <h2 class="section-title mb-8">Entre em Contato</h2>

      <v-row>
        <!-- Coluna esquerda: frase + ícones -->
        <v-col cols="12" md="6" class="contact-message">
          <h3>Vamos conversar!</h3>
          <p>
            Tem um projeto em mente, uma ideia ou até mesmo uma dúvida? <br>
            Será um prazer ouvir você. Envie sua mensagem e responderei o quanto antes!
          </p>

          <div class="tech-icons">
            <v-img
              v-for="(icon, index) in shuffledIcons"
              :key="index"
              :src="icon"
              class="tech-icon"
              width="40"
              height="40"
              contain
            />
          </div>
        </v-col>

        <!-- Formulário à direita -->
        <v-col cols="12" md="6">
          <v-form ref="contactForm" v-model="valid" @submit.prevent="sendEmail">
            <v-row dense>
              <v-col cols="12">
                <v-text-field
                  v-model="form.name"
                  :rules="[rules.required]"
                  label="Nome"
                  outlined
                  dense
                  class="form-field"
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  v-model="form.email"
                  :rules="[rules.required, rules.email]"
                  label="E-mail"
                  outlined
                  dense
                  class="form-field"
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  v-model="form.subject"
                  :rules="[rules.required]"
                  label="Assunto"
                  outlined
                  dense
                  class="form-field"
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-textarea
                  v-model="form.message"
                  :rules="[rules.required]"
                  label="Mensagem"
                  outlined
                  rows="5"
                  class="form-field"
                ></v-textarea>
              </v-col>
              <v-col cols="12" class="text-center mt-4">
                <v-btn :disabled="!valid" color="pink" type="submit">Enviar Mensagem</v-btn>
              </v-col>
            </v-row>
          </v-form>
        </v-col>
      </v-row>

      <v-snackbar v-model="snackbar.show" :color="snackbar.color" top>
        {{ snackbar.text }}
      </v-snackbar>
    </v-container>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import emailjs from '@emailjs/browser'

// Importação dos ícones
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

// Formulário
const contactForm = ref(null)
const valid = ref(false)
const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const snackbar = ref({
  show: false,
  text: '',
  color: ''
})

const rules = {
  required: value => !!value || 'Campo obrigatório',
  email: value => {
    const pattern = /^[^@]+@[^@]+\.[a-zA-Z]{2,}$/
    return pattern.test(value) || 'E-mail inválido'
  }
}

const sendEmail = async () => {
  if (!valid.value) return

  try {
    const templateParams = {
      name: form.value.name,
      email: form.value.email,
      subject: form.value.subject,
      message: form.value.message,
      time: new Date().toLocaleString('pt-BR', { timeZone: 'America/Sao_Paulo' })
    }

    await emailjs.send(
      "service_t888hx9",
      "template_jmjsgub", 
      templateParams, 
      "13invA9zuy66Lo-F7"
    );


    snackbar.value = { show: true, text: 'Mensagem enviada com sucesso!', color: 'green' }
    form.value = { name: '', email: '', subject: '', message: '' }
  } catch (error) {
    snackbar.value = { show: true, text: 'Erro ao enviar a mensagem.', color: 'red' }
    console.error(error)
  }
}

// Lista de ícones
const icons = [
  VueIcon, NuxtIcon, ReactIcon, NextIcon, TSIcon, JSIcon,
  HTMLIcon, CSSIcon, PythonIcon, FastAPIIcon, NodeIcon,
  PostgreSQLIcon, SQLiteIcon, MySQLIcon
]

// Função para embaralhar os ícones
const shuffle = array => array.sort(() => Math.random() - 0.5)
const shuffledIcons = computed(() => shuffle([...icons]))
</script>

<style scoped>
.contact-section {
  padding: 50px 20px;
  background-color: #fff;
  border-radius: 12px;
  margin-top: 20px;
  box-shadow: 0 8px 25px rgba(0,0,0,0.08);
}

.contact-section:hover {
  box-shadow: 0 16px 30px rgba(0,0,0,0.2);
  transform: scale(1.02); 
  cursor: pointer;
}

/* Título */
.section-title {
  font-size: 2.5rem;           
  font-weight: 800;              
  margin-bottom: 20px;  
  margin-top: -20px;        
  text-align: center;            
  color: #e91e63;                
  text-shadow: 1px 1px 3px rgba(0,0,0,0.15);
  text-transform: uppercase;   
}

/* Coluna esquerda */
.contact-message {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  color: #444;
}

.contact-message h3 {
  font-size: 1.9rem;
  font-weight: 700;
  color: #e91e63;
  margin-bottom: 0.8rem;
  letter-spacing: -0.5px;
}

.contact-message p {
  font-size: 1.05rem;
  line-height: 1.6;
  color: #555;
  padding: 15px 20px;
}

/* Ícones das tecnologias */
.tech-icons {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 20px;
}

.tech-icon {
  width: 45px;
  height: 45px;
  object-fit: contain;
  transition: transform 0.2s ease;
}

.tech-icon:hover {
  transform: scale(1.1);
}
</style>