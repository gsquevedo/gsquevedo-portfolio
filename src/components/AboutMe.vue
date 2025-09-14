<template>
  <v-container class="about-me" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" md="8" class="about-text">
        <h2 class="about-title">Sobre Mim</h2>
        <p class="about-description">
          Olá! Meu nome é <strong>Gabriele Quevedo</strong>. Sou graduanda em Ciência da Computação e desenvolvedora Frontend,
          com experiência em criação de interfaces modernas e responsivas. Tenho interesse em desenvolvimento web, integração de APIs
          e design de experiência do usuário, buscando sempre soluções acessíveis e eficientes.  
          Atualmente, venho expandindo meus conhecimentos para o desenvolvimento Backend, explorando novas tecnologias e aplicando
          meus aprendizados em projetos acadêmicos e pessoais. Dessa forma, busco evoluir para uma atuação mais completa no desenvolvimento de aplicações, mantendo meu foco em Frontend e adquirindo habilidades práticas de Backend.
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
</script>

<style scoped>
.about-me {
  padding: 30px;
  background-color: #ffffff;
  color: #222; 
  /* border: 4px solid #e91e63; */
  border-radius: 12px;
  margin-top: -50px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
  transition: all 0.3s ease; 
}

.about-me:hover {
  box-shadow: 0 16px 30px rgba(0,0,0,0.2);
  transform: scale(1.02); 
  cursor: pointer;
}

.about-title {
  font-size: 2.5rem;           
  font-weight: 800;              
  margin-bottom: 20px;          
  text-align: center;            
  color: #e91e63;                
  text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
  text-transform: uppercase;   
}

.about-description {
  font-size: 1.1rem;
  line-height: 1.7;
  text-align: justify; 
}
</style>
