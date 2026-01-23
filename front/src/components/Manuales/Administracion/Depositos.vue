<script setup>
import { ref, onMounted } from "vue";
import { VuePdf, createLoadingTask } from "vue3-pdfjs";
import pdfFile from "../../../assets/admin/Manual.pdf";

const pdfUrl = pdfFile?.default || pdfFile;
const loadingTask = createLoadingTask(pdfUrl);
const numOfPages = ref(0);

onMounted(() => {
    loadingTask.promise.then((pdf) => {
        numOfPages.value = pdf.numPages;
    });
});
</script>


<template>
    <section class="manual-section">
        <h2 class="manual-subtitle">Alta de Clientes</h2>
    </section>
    <VuePdf v-for="page in numOfPages" :key="page" :src="pdfUrl" :page="page" />
</template>

<style scoped></style>