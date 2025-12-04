<template>
  <v-app>
    <Header />
    <v-main class="main-background">
      <v-container>
        <AboutMe />
        <TechStack />
        <!-- <Experience />
        <Projects />
        <Contact /> -->
      </v-container>
    </v-main>
    <!-- <Footer /> -->
  </v-app>
</template>

<script setup>
import Header from './components/Header.vue'
import AboutMe from './components/AboutMe.vue'
import TechStack from './components/TechStack.vue'
// import Experience from './components/Experience.vue'
// import Footer from './components/Footer.vue'
// import Projects from './components/Projects.vue'
// import Contact from './components/Contact.vue'
</script>

<!-- <style scoped>
.main-background {
  background-color: #f5f5f5;
  min-height: 100vh;
  padding-top: 60px;
  padding-bottom: 20px;
}
</style> -->
