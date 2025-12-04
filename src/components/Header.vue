<template>
  <v-app-bar flat class="appbar" elevation="0">
    <v-container class="py-0">
      <v-row align="center" justify="space-between" no-gutters>
        <v-col cols="auto" class="d-flex align-center">
          <span class="logo-text">GABRIELE</span>
        </v-col>

        <!-- Links de Navegação (Desktop) -->
        <v-col cols="auto" class="d-none d-md-flex align-center">
          <div class="links">
            <v-btn
              v-for="link in links"
              :key="link.label"
              variant="text"
              class="nav-link-btn"
              @click="scrollTo(link.href)"
            >
              {{ link.label }}
            </v-btn>
          </div>
        </v-col>
        
        <!-- Hamburger Menu (Mobile) -->
        <v-col cols="auto" class="d-md-none">
          <v-btn icon variant="text" class="menu-icon" @click.stop="drawerOpen = !drawerOpen">
             <v-icon>mdi-menu</v-icon>
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-app-bar>
  
  <!-- Navigation Drawer (Menu Mobile) -->
  <v-navigation-drawer
    v-model="drawerOpen"
    temporary
    location="right"
    class="mobile-drawer"
  >
    <v-list dense>
      <v-list-item
        v-for="link in links"
        :key="link.label"
        link
        @click="handleMobileNav(link.href)"
      >
        <v-list-item-title>{{ link.label }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>

  <v-container class="hero" fluid>
    <v-row align="center" justify="center" class="hero-content">
      
      <v-col cols="12" md="6" class="text-col">
        <h1 class="hero-title">
            <span class="typing-effect">
                {{ displayedTitle }}
            </span>
        </h1>
        
        <p class="hero-intro">{{ introText }}</p>
        
        <v-btn
          class="cta-btn"
          size="large"
          prepend-icon="mdi-download"
          href="#"
          target="_blank"
          rel="noopener"
        >
          Baixar Currículo PDF
        </v-btn>
      </v-col>

      <v-col cols="12" md="6" class="img-col text-center d-flex justify-center justify-md-end">
        <v-avatar size="300" class="hero-avatar">
          <v-img :src="profileImg" alt="Foto de Gabriele" cover />
        </v-avatar>
      </v-col>
      
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import profileImg from '../assets/profile.jpeg';

const drawerOpen = ref(false);

const fullTitle = ref("Desenvolvedora de Software");
const displayedTitle = ref('');
const typingSpeed = 100;    // ms por caractere
const repeatDelay = 5000;   // ms entre repetições

let typingTimer = null;
let repeatTimer = null;
let typingInProgress = false;

const clearTypingTimers = () => {
  if (typingTimer) {
    clearTimeout(typingTimer);
    typingTimer = null;
  }
};

const typeText = () => {
  if (typingInProgress) return;

  typingInProgress = true;
  clearTypingTimers();
  displayedTitle.value = ''; 

  let i = 0;
  const typeChar = () => {
    if (i < fullTitle.value.length) {
      displayedTitle.value += fullTitle.value.charAt(i);
      i++;
      typingTimer = setTimeout(typeChar, typingSpeed);
    } else {
      typingInProgress = false;
      typingTimer = null;
    }
  };

  typeChar();
};

const startTypingLoop = () => {
  // inicia agora
  typeText();

  repeatTimer = setInterval(() => {
    if (!typingInProgress) {
      typeText();
    }
  }, repeatDelay);
};

onMounted(() => {
  startTypingLoop();
});

onBeforeUnmount(() => {
  clearTypingTimers();
  if (repeatTimer) {
    clearInterval(repeatTimer);
    repeatTimer = null;
  }
});

const introText = ref(
  "Olá! Sou Gabriele, desenvolvedora Full Stack e Graduanda em Ciência da Computação. Minha experiência abrange mais de 3 anos criando interfaces reativas (Vue/React) e atualmente aprendizado constante em APIs escaláveis (Python/Django, Node.js). Utilizo minha sólida formação acadêmica para construir soluções digitais inovadoras e confiáveis."
);

const links = ref([
  { label: "Sobre mim", href: "#about" },
  { label: "Tecnologias", href: "#tech" },
  { label: "Experiência", href: "#experience" },
  { label: "Projetos", href: "#projects" },
  { label: "Contato", href: "#contact" },
]);

const scrollTo = (hash) => {
  const el = document.querySelector(hash);
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
};

const handleMobileNav = (hash) => {
  drawerOpen.value = false;
  setTimeout(() => scrollTo(hash), 200);
};

</script>

<style scoped>
.appbar {
  background-color: #ffffff !important;
  border-bottom: 1px solid #eeeeee;
  max-width: 100%; 
  margin: 0 auto;
}

.logo-text {
  font-size: 1.25rem;
  font-weight: 700;
  color: #333333;
  letter-spacing: 0.1rem;
}

.nav-link-btn {
  color: #333333 !important;
  text-transform: none;
  font-weight: 500;
  font-size: 0.95rem;
  margin-left: 12px;
}

.menu-icon {
  color: #333333 !important;
}

.hero {
  background-color: #a7919d;
  min-height: 500px;
  padding: 80px 30px;
  border-radius: 0; 
  margin: 0 !important;
  box-shadow: none;
}

.hero-content {
  max-width: 1100px;
  margin: 0 auto;
}

.hero-title {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 16px;
  margin-top: 20px;
  color: #413a44; 
}

@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: #413a44; } 
}

.typing-effect {
  display: inline-block;
  white-space: nowrap; 
  border-right: 3px solid #413a44; 
  animation: blink-caret 0.75s step-end infinite;
}

.hero-intro {
  font-size: 1.1rem;
  text-align: justify;
  color: #ffffff; 
  margin-bottom: 32px;
  max-width: 1124px;
}

.cta-btn {
  background-color: #413a44 !important;
  color: #ffffff !important;
  text-transform: none; 
  font-weight: 500;
  padding: 8px 24px;
  border-radius: 6px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.cta-btn:hover {
  opacity: 0.9;
  transform: translateY(-2px);
}

.hero-avatar {
  border: 4px solid #ffffff; 
  box-shadow: 0 8px 30px rgba(0,0,0,0.15);
} 

@media (max-width: 959px) {
  .hero {
    text-align: center;
    padding: 50px 20px;
  }

  .hero-title {
    font-size: 2.2rem; 
    line-height: 1.2;
  }

  .hero-intro {
    max-width: none;
    margin: 0 auto 30px auto;
    font-size: 1rem;
  }

  .typing-effect {
    white-space: normal;
  }

  .img-col {
    margin-top: 10px;
    margin-bottom: -30px;
    order: -1;
  }

  .hero-avatar {
    width: 240px !important;
    height: 240px !important;
    margin: 0 auto 20px auto;
  }
}

</style>