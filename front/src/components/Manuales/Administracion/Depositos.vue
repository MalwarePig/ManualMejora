<script setup>
import { ref } from "vue";
import { VuePdf } from "vue3-pdfjs";
import pdfFile from "../../../assets/admin/Manual.pdf";

const pdfUrl = ref(pdfFile);
const page = ref(1);
</script>


<template>
    <section class="manual-section">
        <h2 class="manual-subtitle">Alta de Clientes</h2>
    </section>


    <VuePdf :src="pdfUrl" />
</template>

<style scoped></style>