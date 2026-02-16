<script setup>
import { ref } from 'vue';

const activeLink = ref('inicio');

window.addEventListener('scroll', () => {
    const scrollY = window.scrollY;
    if (scrollY >= 50) {
        document.querySelector('nav').classList.add('activo');
    } else {
        document.querySelector('nav').classList.remove('activo');
    }
})

</script>
<template>
    <nav class="activo">
        <ul>
            <li>
                <a href="#inicio" :class="{ active: activeLink == 'inicio' }" @click="activeLink = 'inicio'">Inicio</a>
            </li>
            <li>
                <a href="#proyectos" :class="{ active: activeLink == 'proyectos' }"
                    @click="activeLink = 'proyectos'">Proyectos</a>
            </li>
            <li>
                <a href="#tecnologias" :class="{ active: activeLink == 'tecnologias' }"
                    @click="activeLink = 'tecnologias'">Tecnologias</a>
            </li>
            <li>
                <a href="#contacto" :class="{ active: activeLink == 'contacto' }"
                    @click="activeLink = 'contacto'">Contacto</a>
            </li>
        </ul>
    </nav>
</template>
<style scoped>
nav {
    position: fixed;
    top: 20px;
    padding: 7px 20px;
    border-radius: var(--card-radius-border);
    z-index: 10;

    ul {
        display: flex;
        gap: 16px;
        list-style: none;
    }
}

.activo {
    background-color: #281349;
    border: 1px solid var(--card-color-border);
}

a {
    color: var(--color-primary);
    font-size: 1.1em;
    transition: color .2s ease;
}

a:hover {
    color: var(--color-third);
}

.active {
    color: var(--color-third);
}

@media (max-width: 800px) {
    a {
        font-size: 1em !important;
    }
}
</style>