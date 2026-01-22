<template>
    <div class="manual">
        <h1 class="manual-title">Manual de Procesos – MejoraSoft</h1>
        <section class="manual-section">
            <h2 class="manual-subtitle">Alta de Clientes</h2>
            <p class="manual-text">
                Describe el proceso para registrar clientes, incluyendo datos fiscales, configuración comercial,
                direcciones, contactos y cuentas bancarias.
            </p>
            <p class="manual-text"> <span>Comercial</span> >> <span>Clientes</span> >> <span>Alta de Clientes</span></p>
        </section>

        <figure class="manual-image">
            <img src="../../../assets/img/RH/Clientes.png" alt="Ejemplo de diagrama" />
        </figure>

        <section class="manual-section">
            <h2 class="manual-subtitle">Direcciones</h2>
            <p class="manual-text">
                Catálogo de direcciones reutilizables, generales o específicas por cliente, con comportamiento dinámico
                según el país seleccionado.
            </p>
        </section>

        <section class="manual-section">
            <h2 class="manual-subtitle">Facturación</h2>
            <p class="manual-text">
                Proceso de generación de facturas mediante notas de venta o carta porte, con validaciones fiscales
                y opciones de timbrado.
            </p>
        </section>

        <figure class="manual-image">
            <img src="../../../assets/img/RH/Clientes.png" alt="Ejemplo de diagrama" />
            <!-- <figcaption class="manual-caption">Ejemplo de imagen</figcaption> -->
        </figure>
    </div>
</template>

<script setup>
// Componente informativo reutilizable para manuales
</script>

<style scoped>
span {
    color: tomato;
    font-weight: bold;
    font-size: 1.2rem;
}
</style>