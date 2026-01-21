<script setup>
import { ref } from 'vue';
import AccordionMenu from './components/sidebar/AccordionMenu.vue';
import Facturacion from './components/Manuales/Administracion/Facturacion.vue'

var pageActive = ref('DEMO')
function AquiEscuchaPadre(data) {
  console.log("Aqui recibir Titulo " + Object.values(data))

  pageActive.value = data
}


</script>

<template>
  <div class="app-container">
    <div class="sidebar">
      <h2>Menu</h2>
      <AccordionMenu :menuItems="menuData" @showPage="AquiEscuchaPadre" />
    </div>
    <div class="main-content">
      <h1>MejoraSoft</h1>
      <p>Sección de información.</p>
      <p>{{ pageActive }}</p>
    </div>
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  width: 100%;
  height: 100vh;
  font-family: 'Inter', sans-serif;
  background-color: #111827;
  /* Dark background */
  color: #f3f4f6;
  /* Light text */
  overflow: hidden;
}

.sidebar {
  width: 320px;
  background-color: #1f2937;
  /* Slightly lighter dark for sidebar */
  padding: 20px;
  border-right: 1px solid #374151;
  /* Dark border */
  overflow-y: auto;
  display: flex;
  flex-direction: column;
}

.sidebar h2 {
  margin-top: 0;
  margin-bottom: 20px;
  color: #f9fafb;
  font-size: 1.5rem;
}

.main-content {
  flex: 1;
  padding: 40px;
  width: 100%;
  overflow-y: auto;
  background-color: #111827;
}

h1 {
  color: #f9fafb;
}

p {
  color: #9ca3af;
}
</style>
