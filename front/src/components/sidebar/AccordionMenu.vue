<script setup>
import { ref } from 'vue';
const emit = defineEmits(['ShowInfo'])

var data = ref([
    {
        Titulo: 'Administracion',
        paginas: ['Facturacion', 'Depositos', 'Transferencias'],
        visible: false
    },
    {
        Titulo: 'Operaciones',
        paginas: ['Programaciones', 'Viajes', 'Carta Porte'],
        visible: false
    },
    {
        Titulo: 'Compras',
        paginas: ['OC', 'Proveedores'],
        visible: false
    }
])


function isShowF(index) {
    data.value[index].visible = !data.value[index].visible
   
}

function loadPage(params) {
     emit('showPage', params)
     console.log(params)
}

</script>
<template>
    <div class="div-side-bar">
        <div class="header-bar" v-for="(value, index) in data" :key="index">
            <div @click="isShowF(index)">
                <p>{{ value.Titulo }}</p>
            </div>


            <div class="body-bar" v-for="subvalue in value.paginas" :key="subvalue" v-show="value.visible" @click="loadPage(subvalue)">
                <p>{{ subvalue }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.div-side-bar {
    background-color: #242424;
}

.header-bar {
    background-color: #180b17;
    display: flex;
    flex-direction: column;
    font-size: 1rem;
    padding: 1px;
    border: 1px #3f3c3f solid;
}

.header-bar p {
    margin: 5px;
}

.body-bar {
    background-color: #a37ca0;
    margin: 0;
    padding: 0;
    border: 1px #3f3c3f solid;
}

.body-bar:hover {
    background-color: #8a6487;
}

/* s */
</style>