<script setup>

</script>

<template>
    <div class="container">
        <h1>MejoraSoft</h1>
        <p>Manual de uso.</p>
        <div class="portada">
            <img src="../../assets/img/Portada1.png" alt="Portada">
        </div>

    </div>
</template>

<style scoped>
p {
    color: #0b0b0b;
    font-size: 2rem;
    margin: 0;
}

h1 {
    color: #0b0b0b;
    margin: 0;
}

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.portada {
    width: 40%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.portada img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: drop-shadow(0 0 10px rgba(0, 0, 0, 0.8));
    mask-image: linear-gradient(black 90%, transparent);
}
</style>