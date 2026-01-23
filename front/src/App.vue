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

function helpWindow() {
    helpActive.value = !helpActive.value
}

</script>

<template>
    <button @click="helpWindow()">Help</button>
    <Navbar @showHelp="helpWindow" />
    <div class="app-container">
        <div class="Help" v-if="helpActive">
            <h2>Help</h2>
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
    width: 100%;
    height: 100vh;
    font-family: 'Inter', sans-serif;
    background-color: #ebebeb;
    /* Dark background */
    color: #f3f4f6;
    /* Light text */
    overflow: hidden;
}

.Manuals {
    display: flex;
    overflow: hidden;
    width: 100%;
    height: 100vh;
}

.sidebar {
    width: 320px;
    background-color: #ebebeb;
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
    color: #0b0b0b;
    font-size: 1.5rem;
}

.main-content {
    flex: 1;
    padding: 40px;
    width: 100%;
    overflow-y: auto;
    background-color: #ebebeb;
}

h1 {
    color: #0b0b0b;
}

p {
    color: #0b0b0b;
}
</style>