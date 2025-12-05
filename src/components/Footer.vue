<template>
  <footer class="footer">
    <div class="footer-content">
      <p class="footer-text">
        © 2025 {{ name }} — Desenvolvido com Vue.js + Vuetify
      </p>
    </div>
  </footer>
</template>

<script setup>
const name = "Gabriele Quevedo";
</script>

<style scoped>
.footer {
  width: 100%;
  padding: 24px 0;

  background: linear-gradient(135deg, #413a44 0%, #5a4e5a 50%, #a7919d 100%);
  color: #ffffff;

  display: flex;
  justify-content: center;
  align-items: center;

  box-shadow: 0 -4px 18px rgba(0, 0, 0, 0.1);
}

.footer-content {
  text-align: center;
  width: 100%;
}

.footer-text {
  font-size: 1rem;
  font-weight: 300;
  letter-spacing: 0.3px;
  opacity: 0.95;
  margin: 0;
}
</style>
