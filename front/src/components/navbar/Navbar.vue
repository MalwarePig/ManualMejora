<script setup>


</script>
<template>
    <div class="navbar">
        <div class="navbar-item">
            <p>Manual</p>
        </div>
        <div class="navbar-item">
            <p>Ayuda</p>
        </div>
    </div>
</template>

<style scoped>
.navbar {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #ebebeb;
    gap: 10px;
    padding: 5px;
    box-shadow: 2px 2px 5px #615e61;
    margin-bottom: 5px;
}

.navbar-item {
    border-radius: 8px;
    height: 30px;
    width: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.navbar-item:hover {
    cursor: pointer;
    color: #000;
    text-decoration: underline;
}
</style>