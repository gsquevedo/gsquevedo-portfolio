<template>
  <v-app>
    <Header />
    <v-main class="main-background">
      <v-container>
        
        <AboutMe />

        <v-row class="mt-10" align="stretch">
          <v-col cols="12" md="6">
            <TechStack />
          </v-col>

          <v-col cols="12" md="6">
            <Experience />
          </v-col>
        </v-row>
        <Projects />
        <Contact />
      </v-container>
      <Footer />
    </v-main>
  </v-app>
</template>

<script setup>
import Header from './components/Header.vue'
import AboutMe from './components/AboutMe.vue'
import TechStack from './components/TechStack.vue'
import Experience from './components/Experience.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
</script>

<style>
</style>
