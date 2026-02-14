<script setup>
import fotoPerfil from '@/assets/foto-perfil.webp'

</script>
<template>
    <section id="first" class="first-section">
        <div class="info-section">
            <p class="txt-name">
                <span class="txt-var">{</span> Hola soy, Obed Aquino <span class="txt-var">}</span>
            </p>
            <h1>Desarrollador
                <span class="letter-tag">
                    < Full Stack Jr />
                </span>
            </h1>
            <p class="txt-info">
                Ayudo a transformar ideas en aplicaciones web funcionales.
                Disfruto construir la lógica detrás de sistemas web, APIs y bases de datos.
            </p>
            <a class="btn btn-primary">Ver proyectos</a>
            <a href="/CV_Obed_Aquino_Desarrollador_Full_Stack_Junior.pdf" download="CV_Obed_Aquino.pdf"
                class="btn btn-secondary">
                Descarcar CV
            </a>
        </div>
        <div class="perfil-section">
            <img :src="fotoPerfil" alt="Foto de perfil" class="ft-perfil">
        </div>
    </section>
</template>
<style scoped>
.first-section {
    width: 90%;
    min-height: 400px;
    display: grid;
    grid-template-columns: 2fr 1fr;
    justify-items: center;
    padding: 26px 52px;
    background: linear-gradient(180deg, rgba(12, 15, 33, 1) 8%, rgba(20, 27, 72, 1) 86%);
    border: 1px solid var(--card-color-border);
    border-radius: var(--card-radius-border);
    transition: transform 1s ease, box-shadow 1s ease;

    &:hover {
        border-color: rgba(17, 82, 212, 0.3);
        box-shadow: var(--box-shadow-secondary);

    }
}

.txt-name {
    font-size: 1.5em;
    font-weight: 600;
    color: var(--color-primary);
    text-decoration: none;
}

.txt-var {
    background-color: var(--card-color-border);
    color: var(--color-third);
    font-weight: 700;
    padding: 5px 10px;
    border-radius: var(--card-radius-border);
}

.info-section {
    align-self: center;

    h1 {
        font-size: 2.5em;
        line-height: 1.1;
        color: var(--color-primary);
    }

    .letter-tag {
        color: var(--color-secondary);
        font-weight: 800;
    }

    .txt-info {
        color: var(--color-third);
        font-size: 1.4em;
    }
}

/* esto genera espacio entre los elementos del contenedor sin usar flexbox */
.info-section>* {
    margin-bottom: 10px;
}

.btn {
    display: inline-flex;
    line-height: 1;
    margin: 5px 0;
    padding: 10px;
    font-size: 1em;
    font-weight: 600;
    cursor: pointer;
    border-radius: var(--card-radius-border);
    transition: .3s all ease-in-out;
    text-decoration: none;
    color: var(--color-primary);

    &:hover {
        transform: translateY(-1px);
        box-shadow: var(--box-shadow-secondary);
    }
}

.btn-primary {
    background-color: var(--color-secondary);
    border: .1px solid var(--color-secondary);
    margin-right: 15px;
}

.btn-secondary {
    background-color: transparent;
    border: .1px solid var(--color-primary);
}

.perfil-section {
    align-self: center;
    text-align: end;
    width: 100%;

    .ft-perfil {
        max-width: 300px;
        object-fit: cover;
        border-radius: 50%;
        border: 5px solid var(--card-color-border);
        margin-bottom: 5px;
        transition: .2s all ease-in-out;

        &:hover {
            box-shadow: var(--box-shadow-secondary);
        }
    }

    p {
        font-size: 1.8em;
        font-weight: 500;
        color: var(--color-primary);
    }
}

@media (max-width: 1150px) {
    .info-section>h1 {
        display: flex;
        flex-direction: column;
    }

    .txt-info {
        max-width: 90%;
        font-size: 1em;
    }

    .ft-perfil {
        width: 260px;
    }
}

@media (max-width: 820px) {
    .first-section {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .txt-name {
        font-size: 1.3em;
    }

    .info-section {
        order: 2;
        text-align: center;

        h1 {
            font-size: 1.9em;
        }
    }

    .info-section>* {
        margin-bottom: 15px;
    }

    .txt-info {
        max-width: 95%;
        font-size: 1.2em !important;
    }

    .perfil-section {
        order: 1;
        text-align: center;
    }

    .ft-perfil {
        width: 220px;
        border-radius: 50% !important;
    }

    .btn {
        display: block;
        margin-right: 0;
        padding: 8px;
        font-size: 1em;
    }
}

@media (max-width: 460px) {
    .txt-name {
        font-size: 1.1em;
    }

    h1 {
        font-size: 1.7em !important;
    }

    .txt-info {
        max-width: 95%;
        font-size: 1.1em !important;
    }

    .btn {
        font-size: 15px !important;
    }
}
</style>