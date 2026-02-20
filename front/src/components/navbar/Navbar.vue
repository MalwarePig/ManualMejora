<script setup>
const emit = defineEmits(['showHelp'])

</script>
<template>
    <div class="navbar">
        <div class="navbar-left">
            <!-- Logo Icon/Text -->
            <img class="logo" src="../../assets/logo/logo.png" alt="">
            <span class="logo-text">MejoraSoft</span>
        </div>

        <div class="navbar-center">
            <div class="navbar-item">
                <button @click="emit('showHelp', false)">Manual</button>
            </div>
            <div class="navbar-item">
                <button @click="emit('showHelp', true)">Ayuda</button>
            </div>
        </div>

        <div class="navbar-right">
            <!-- WhatsApp Icon -->
            <a href="https://wa.me/8126156944" target="_blank" class="whatsapp-link">
                <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="#25D366"
                    stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                    <path
                        d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z">
                    </path>
                </svg>
            </a>
        </div>
    </div>
</template>

<style scoped>
.navbar {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    background-color: #083cae;
    padding: 12px 20px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    box-sizing: border-box;
}

.navbar-left {
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

.navbar-center {
    display: flex;
    justify-content: center;
    gap: 15px;
}

.navbar-right {
    display: flex;
    justify-content: flex-end;
}

.logo {
    width: 32px;
    height: 32px;
    background-color: #615e61;
    border-radius: 50%;
    padding: 2px;
    margin-right: 12px;
}

.logo-text {
    color: white;
    font-weight: 700;
    font-size: 1.25rem;
    letter-spacing: -0.025em;
}

.navbar-item {
    border-radius: 8px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.2s ease;
}

button {
    background-color: #083cae;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    margin: 0;
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 6px;
    padding: 6px 16px;
    cursor: pointer;
    font-weight: 500;
    transition: all 0.2s ease;
}

button:hover {
    background-color: #0c4ce0;
    transform: translateY(-1px);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.4);
}

button:active {
    transform: translateY(0);
}

.whatsapp-link {
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.whatsapp-link:hover {
    transform: scale(1.15) rotate(5deg);
    filter: drop-shadow(0 0 8px rgba(37, 211, 102, 0.4));
}

.navbar-item:hover {
    cursor: pointer;
}
</style>