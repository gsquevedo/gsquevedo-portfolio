<template>
  <v-container id="contact" class="contact-section fade-wrapper" fluid>
    <v-row justify="center">
      <v-col cols="12" md="10" lg="8">

        <div class="title-wrapper fade-up">
          <h2 class="contact-title">Entre em Contato</h2>
          <div class="title-underline"></div>
        </div>

        <v-row class="contact-grid fade-up">

          <v-col cols="12" md="5" class="left" style="--delay: 150ms;">
            <h3 class="left-title">Vamos Conversar</h3>

            <p class="left-text">
              Tem um projeto, uma dúvida ou apenas quer trocar ideias sobre tecnologia?
              <br/>Será um prazer falar com você!
            </p>

            <div class="contacts-wrapper" style="--delay: 300ms;">
              <a
                v-for="contact in contacts"
                :key="contact.name"
                :href="contact.url"
                class="contact-item"
                target="_blank"
                rel="noopener"
              >
                <img :src="contact.icon" class="contact-icon" />
                <div class="contact-labels">
                  <span class="contact-name">{{ contact.name }}</span>
                  <span class="contact-value">{{ contact.value }}</span>
                </div>
              </a>
            </div>
          </v-col>

          <v-col cols="12" md="7" class="form-col" style="--delay: 450ms;">
            <div class="form-card">
              <v-form ref="contactForm" v-model="valid" @submit.prevent="sendEmail">

                <v-text-field
                  v-model="form.name"
                  :rules="[rules.required]"
                  label="Nome"
                  variant="outlined"
                  class="form-field"
                  color="#413a44"
                />

                <v-text-field
                  v-model="form.email"
                  :rules="[rules.required, rules.email]"
                  label="E-mail"
                  variant="outlined"
                  class="form-field"
                  color="#413a44"
                />

                <v-text-field
                  v-model="form.subject"
                  :rules="[rules.required]"
                  label="Assunto"
                  variant="outlined"
                  class="form-field"
                  color="#413a44"
                />

                <v-textarea
                  v-model="form.message"
                  :rules="[rules.required]"
                  label="Mensagem"
                  variant="outlined"
                  rows="5"
                  class="form-field"
                  color="#413a44"
                />

                <div class="button-wrapper">
                  <v-btn type="submit" :disabled="!valid" class="send-btn">
                    Enviar Mensagem
                  </v-btn>
                </div>

              </v-form>
            </div>
          </v-col>

        </v-row>

        <v-snackbar v-model="snackbar.show" :color="snackbar.color" top>
          {{ snackbar.text }}
        </v-snackbar>

      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import emailjs from '@emailjs/browser'

import LinkedinIcon from '../assets/linkedin.png'
import EmailIcon from '../assets/gmail.png'
import PhoneIcon from '../assets/whatsapp.png'
import MediumIcon from '../assets/medium.png'

const contacts = [
  {
    name: "E-mail",
    value: "gsquevedo@gmail.com",
    url: "mailto:gsquevedo@gmail.com",
    icon: EmailIcon
  },
  {
    name: "LinkedIn",
    value: "Gabriele Quevedo",
    url: "https://www.linkedin.com/in/gsquevedo/",
    icon: LinkedinIcon
  },
  {
    name: "Medium",
    value: "Gabriele Quevedo",
    url: "https://medium.com/@gabrielequevedo",
    icon: MediumIcon
  },
  {
    name: "WhatsApp",
    value: "Chamar no WhatsApp",
    url: "https://wa.me/5555997276535",
    icon: PhoneIcon
  }
]

const contactForm = ref(null)
const valid = ref(false)

const form = ref({
  name: "",
  email: "",
  subject: "",
  message: ""
})

const snackbar = ref({ show: false, text: "", color: "" })

const rules = {
  required: v => !!v || "Campo obrigatório",
  email: v => /^[^@]+@[^@]+\.[a-zA-Z]{2,}$/.test(v) || "E-mail inválido"
}

const sendEmail = async () => {
  if (!valid.value) return
  try {
    await emailjs.send(
      "service_t888hx9",
      "template_jmjsgub",
      { ...form.value, time: new Date().toLocaleString("pt-BR") },
      "13invA9zuy66Lo-F7"
    )

    snackbar.value = { show: true, text: "Mensagem enviada com sucesso!", color: "green" }
    form.value = { name: "", email: "", subject: "", message: "" }

  } catch (error) {
    snackbar.value = { show: true, text: "Erro ao enviar mensagem.", color: "red" }
    console.error(error)
  }
}

onMounted(() => {
  const section = document.querySelector("#contact")
  const reveal = () => {
    if (window.scrollY + window.innerHeight >= section.offsetTop + 160) {
      section.querySelectorAll(".fade-up").forEach(el => el.classList.add("visible"))
      window.removeEventListener("scroll", reveal)
    }
  }
  window.addEventListener("scroll", reveal)
  reveal()
})
</script>

<style scoped>
.contact-section {
  padding-top: 20px !important;
  padding-bottom: 20px !important;
}

.title-wrapper {
  text-align: center;
  margin-bottom: 25px;
}

.contact-title {
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

.contact-grid {
  display: flex;
  align-items: flex-start;
  margin-top: 25px;
}

.left-title {
  font-size: 1.7rem;
  font-weight: 700;
  color: #413a44;
  margin-bottom: 8px;
}

.left-text {
  color: #555;
  font-size: 1.05rem;
  line-height: 1.6;
  margin-bottom: 25px;
}

.contacts-wrapper {
  display: flex;
  flex-direction: column;
  gap: 18px;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 14px;
  text-decoration: none;
  padding: 10px 12px;
  border-radius: 10px;
  transition: 0.25s ease;
}

.contact-item:hover {
  background-color: #f1e7f0;
  transform: translateX(6px);
}

.contact-icon {
  width: 34px;
  height: 34px;
}

.contact-labels {
  display: flex;
  flex-direction: column;
}

.contact-name {
  color: #413a44;
  font-weight: 700;
}

.contact-value {
  color: #6d6270;
  font-size: 0.95rem;
}

/* FORM */
.form-card {
  background: #ffffff;
  padding: 20px;
  border-radius: 14px;
  box-shadow: 0 4px 14px rgba(0,0,0,0.08);
  border: 1px solid #f0e8ef;
}

.form-field {
  margin-bottom: 5px;
}

.v-input.form-field,
.v-textarea.form-field {
  max-width: 680px;
  width: 100%;
}

.send-btn {
  background-color: #a7919d !important;
  color: white;
  font-weight: 700;
  letter-spacing: 0.6px;
  padding: 12px 20px;
  border-radius: 12px;
  transition: 0.25s ease;
}

.send-btn:hover {
  background-color: #2f2930 !important;
}

.fade-up {
  opacity: 0;
  transform: translateY(20px);
  transition: 0.7s ease;
}

.visible {
  opacity: 1 !important;
  transform: translateY(0) !important;
}
</style>
