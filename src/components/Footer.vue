<template>
  <v-footer app color="grey-darken-4" dark>
    <v-col class="text-center">
      © 2025 {{ name }} - Desenvolvido com Vue.js + Vuetify
    </v-col>
  </v-footer>
</template>

<script setup>
const name = "Gabriele Quevedo";
</script>

<style scoped>
.v-footer {
  background: linear-gradient(135deg, #f06292 0%, #e91e63 50%, #d81b60 100%) !important;
  color: #fff;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}
</style>
