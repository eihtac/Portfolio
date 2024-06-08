<template>
    <div :class="['footer', { hidden: isHidden }]">
        <div class="links">
            <a target="_blank" href="https://github.com/eihtac"><img src="../assets/img/github-icon.png" alt="icône github"></a>
            <a target="_blank" href="https://fr.linkedin.com/"><img src="../assets/img/linkedin-icon.png" alt="icône linkedin"></a>
        </div>
        <small>Mis à jour le <time datetime="2024-06-05">05.06.2024</time></small>
    </div>
</template>

<script setup>
    defineProps({
        isHidden: {
            type: Boolean,
            default: false
        }
    });
</script>

<style scoped>
.footer {
    background-color: #0D141F;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 100;
    position: fixed;
    bottom: 0;
}

.links {
    margin: 10px;
}

a {
    margin: 5px;
}

img {
    width: 28px;
}

small {
    color: #FFD60A;
}

.hidden {
    opacity: 0;
    pointer-events: none;
}
</style>
