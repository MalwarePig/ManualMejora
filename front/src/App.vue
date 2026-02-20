<script setup>
//Importaciones
import { ref, shallowRef } from 'vue';
import AccordionMenu from './components/sidebar/AccordionMenu.vue';
import Facturacion from './components/Manuales/Administracion/Facturacion.vue'
import Depositos from './components/Manuales/Administracion/Depositos.vue'
import Transferencias from './components/Manuales/Administracion/Transferencias.vue'
import Home from './components/Home/Home.vue'
import Navbar from './components/navbar/Navbar.vue'
import RH from './components/Manuales/RH/RH.vue'
import Clientes from './components/Manuales/Comercial/Clientes.vue'
import Ayuda from './components/Ayuda/main/main.vue'

//Variables
var pageActive = shallowRef(Home)

const routes = {
    'Facturacion': Facturacion,
    'Depositos': Depositos,
    'Transferencias': Transferencias,
    'RH': RH,
    'Clientes': Clientes
}

var helpActive = ref(false)

//Funciones
function AquiEscuchaPadre(data) {
    pageActive.value = routes[data]
}

function helpWindow(data) {
    helpActive.value = data
}

</script>

<template>
    <Navbar @showHelp="helpWindow" />
    <div class="app-container">
        <div class="Help" v-if="helpActive">
            <Ayuda />
        </div>

        <div class="Manuals" v-else>
            <div class="sidebar">
                <h2>Menu</h2>
                <AccordionMenu :menuItems="menuData" @showPage="AquiEscuchaPadre" />
            </div>
            <div class="main-content">
                <component :is="pageActive" v-if="pageActive" />
            </div>
        </div>
    </div>
</template>

<style scoped>
.app-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100vh;
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
    background-color: #f3f4f6;
    color: #1f2937;
    overflow: hidden;
}

.Manuals {
    display: flex;
    overflow: hidden;
    width: 100%;
    flex: 1;
}

.Help {
    width: 100%;
    flex: 1;
}

.sidebar {
    width: 280px;
    background-color: #2EBF1F;
    padding: 20px 0;
    border-right: 1px solid rgba(0, 0, 0, 0.1);
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    box-shadow: 4px 0 10px rgba(0, 0, 0, 0.05);
    z-index: 10;
}

.sidebar h2 {
    margin: 0 20px 15px 20px;
    color: white;
    font-size: 1.1rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
}

.main-content {
    flex: 1;
    padding: 30px 40px;
    width: 100%;
    overflow-y: auto;
    background-color: #ffffff;
}

h1 {
    color: #111827;
    margin-top: 0;
}

p {
    color: #374151;
    line-height: 1.6;
}
</style>