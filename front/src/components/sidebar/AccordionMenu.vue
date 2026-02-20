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
            <div class="header-title" @click="isShowF(index)">
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
    background-color: #2EBF1F;
    border-radius: 12px;
    padding: 8px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
    margin: 10px;
}

.header-bar {
    background-color: #ffffff;
    color: #1f2937;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    font-size: 0.95rem;
    padding: 0;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    margin-bottom: 8px;
    transition: all 0.2s ease;
    border: 1px solid transparent;
}

.header-bar:last-child {
    margin-bottom: 0;
}

.header-bar .header-title {
    padding: 12px 16px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.header-bar:hover {
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.header-bar:hover .header-title p {
    font-weight: 600;
    color: #2EBF1F;
}

.header-bar p {
    margin: 0;
}

.body-bar {
    background-color: #f9fafb;
    margin: 4px 12px 8px 12px;
    padding: 10px 14px;
    border: 1px solid #e5e7eb;
    border-radius: 8px;
    transition: all 0.2s ease;
    cursor: pointer;
    font-size: 0.9rem;
    color: #4b5563;
}

.body-bar:hover {
    background-color: #fff9c4;
    border-color: #f7f58f;
    color: #111827;
    padding-left: 18px;
}

.body-bar:last-child {
    margin-bottom: 12px;
}

.menuActive {
    border-color: #2cbf1f;
    background-color: #fff;
    box-shadow: 0 4px 12px rgba(44, 191, 31, 0.15);
}

.menuActive .header-title p {
    font-weight: 700;
    color: #2cbf1f;
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
