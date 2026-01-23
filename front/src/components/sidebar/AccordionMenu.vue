<script setup>
import { ref } from 'vue';
const emit = defineEmits(['showPage'])

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
    },
    {
        Titulo: 'Recursos Humanos',
        paginas: ['RH'],
        visible: false
    },
    {
        Titulo: 'Comercial',
        paginas: ['Clientes'],
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
        <div class="header-bar" :class="{ 'menuActive': value.visible }" v-for="(value, index) in data" :key="index">
            <div @click="isShowF(index)">
                <p>{{ value.Titulo }}</p>
            </div>


            <transition name="slide-fade">
                <div v-show="value.visible">
                    <div class="body-bar" v-for="subvalue in value.paginas" :key="subvalue" @click="loadPage(subvalue)">
                        <p>{{ subvalue }}</p>
                    </div>
                </div>
            </transition>
        </div>
    </div>
</template>

<style scoped>
.div-side-bar {
    background-color: #ebebeb;
    /*    border: 1px #3f3c3f solid; */
    border-radius: 8px;
    padding: 5px;
    box-shadow: 2px 2px 5px #615e61;
}

.header-bar {
    background-color: #ebebeb;
    color: #3f3c3f;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    font-size: 1rem;
    padding: 1px;
    /*  border: 1px #3f3c3f solid; */
    box-shadow: 2px 2px 5px #615e61;
    margin: 5px;
    padding: 5px;
}

.header-bar:hover>div>p {
    cursor: pointer;
    font-weight: bold;
}


.header-bar p {
    margin: 5px;
}

.body-bar {
    background-color: #e7e3e7;
    margin: 0;
    padding: 0;
    border: 1px #bebbbe solid;
    border-radius: 8px;
}

.body-bar:hover {
    background-color: #a19fa1;
}

.menuActive {
    border: 1px #2cbf1f solid;
}

.menuActive>div>p {
    font-weight: bold;
}

/* Animación de despliegue (Accordion) */
.slide-fade-enter-active,
.slide-fade-leave-active {
    transition: all 0.4s ease;
    max-height: 500px;
    overflow: hidden;
    opacity: 1;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    max-height: 0;
    opacity: 0;
}
</style>
