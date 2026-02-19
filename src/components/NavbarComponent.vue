<script setup>
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
    <nav>
        <ul>
            <li>
                <a href="#inicio">Inicio</a>
            </li>
            <li>
                <a href="#proyectos">Proyectos</a>
            </li>
            <li>
                <a href="#tecnologias">Tecnologias</a>
            </li>
            <li>
                <a href="#contacto">Contacto</a>
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

@media (max-width: 800px) {
    a {
        font-size: 1em !important;
    }
}
</style>