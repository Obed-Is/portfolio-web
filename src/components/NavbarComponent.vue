<script setup>

</script>
<template>
    <nav>
        <a href="#first" class="txt-name"><em class="txt-var">const</em> Obed Aquino</a>
        <ul>
            <li><a href="#start">Inicio</a></li>
            <li><a href="#proyects">Proyectos</a></li>
            <li><a href="#technologies">Tecnologias</a></li>
            <li><a href="#contact" class="contact">Contacto</a></li>
        </ul>
    </nav>
</template>
<style scoped>
nav {
    position: fixed;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 70px;
    width: 100%;
    padding: 0 50px;
    border-bottom: 1px solid var(--card-color-border);
    top: 0;
    color: var(--color-primary);
    background: rgba(12, 15, 33, 0.6);
    backdrop-filter: blur(5px);
}

.txt-name {
    font-size: 1.1em;
    font-weight: 500;
    color: var(--color-primary);
    text-decoration: none;
}

.txt-var {
    background-color: var(--card-color-border);
    color: var(--color-third);
    text-transform: uppercase;
    padding: 5px 10px;
    border-radius: var(--card-radius-border);
}

ul {
    display: flex;
    gap: 40px;
}

li {
    list-style: none;
}

a {
    color: var(--color-primary);
    font-weight: 500;
    transition: color .3s ease;

    &:hover {
        color: var(--color-third);
    }
}

.contact {
    background-color: var(--color-secondary);
    padding: 7px;
    border-radius: var(--card-radius-border);
    color: var(--color-primary) !important;
}
</style>