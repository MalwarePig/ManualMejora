<script setup>
import { ref } from 'vue'
import Folios from '../cards/Folios.vue'
import sat from '../../../assets/data/sat.json'
import CCP from '../../../assets/data/CCP.json'

var data = [...sat, ...CCP]
var inputFilter = ref('')
var filtro = ref(data)

function filterData() {
    filtro.value = data.filter(item =>
        item.codigo.includes(inputFilter.value) ||
        (item.detalle && item.detalle.includes(inputFilter.value))
    )
}

</script>

<template>
    <div class="main-container">
        <div class="buscador">
            <div class="titulo">
                <h2>Catálogo de errores SAT</h2>
                <p>Comprobante fiscal digital por Internet. Versión 4.0</p>
            </div>
            <input type="text" placeholder="Buscar" v-model="inputFilter" @input="filterData">
        </div>
        <div class="contenido">
            <Folios :codigo="item.codigo" :descripcion="item.descripcion" v-for="(item, index) in filtro" :key="index"
                :indice="index" :visible="item.visible" :detalle="item.detalle" />
        </div>
    </div>
</template>

<style scoped>
.main-container {
    color: #e40404;
    background-color: #ffffff;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
}

.titulo {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 0;
    margin: 10px;
}

h2 {
    margin: 0;
}

p {
    margin: 0;
}

.buscador {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 40%;
}

.buscador input {
    width: 90%;
}

.contenido {
    padding: 15px 10px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    width: 60%;
    gap: 5px;
    overflow-y: auto;
    overflow-x: hidden;
    height: 60%;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
    background-color: #f3f3f3;
}

input {
    background-color: #fff;
    color: #000;
    padding: 10px;
    border-radius: 8px;
    border: 1px solid #ccc;
}
</style>