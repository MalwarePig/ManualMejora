<script setup>
import { ref } from 'vue'
const props = defineProps({
    codigo: String,
    descripcion: String,
    detalle: String,
    indice: String,
    visible: Boolean
})

function showDetails(indice) {
    var cards = document.getElementsByName(indice)
    visible.value = !visible.value
    cards[0].classList.toggle('detalles_activated')
}

var visible = ref(props.visible)

</script>

<template>
    <div class="card" @click="showDetails(props.indice)" :name="props.indice">
        <div class="titulo">
            <p>{{ codigo }} - {{ descripcion }}</p>
        </div>
        <div class="detalles" v-if="visible">
            <p>{{ detalle }}
            </p>
        </div>
    </div>
</template>

<style scoped>
.card {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
    border-radius: 8px;
    width: 100%;
    color: #000;
    padding: 2px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: rgb(226, 226, 226);
}

.card:hover {
    cursor: pointer;
    /* background-color: #f5f5f5; */
    background-color: #26275e;
}

.card:hover p {
    color: #fff;
}

p {
    font-size: 1rem;
    color: #000;
}

.titulo {
    padding: 10px;
}

.detalles {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
    border-top: 1px solid #00000027;
}

.detalles_activated {
    background-color: #f5f5f5;
    border: 1px #2cbf1f solid;
}
</style>