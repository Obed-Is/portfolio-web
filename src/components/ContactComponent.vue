<script setup>
import linkedinIcon from '@/assets/linkedin.svg'
import gmailIcon from '@/assets/gmail.svg'
import githubIcon from '@/assets/svgTecnologias/github_dark.svg'

const emailContact = {
    email: "obedaquino71@gmail.com",
    body: "Hola Obed, me interesa trabajar contigo."
}

const gmailLink = `https://mail.google.com/mail/?view=cm&to=${emailContact.email}&body=${emailContact.body}`
</script>
<template>
    <section id="contacto">
        <h2>Contacto</h2>
        <p class="txt-info">¿Quieres que trabajemos juntos? ¡Hablemos!</p>
        <div class="container-contact">
            <a href="https://www.linkedin.com/in/obed-aquino-mart%C3%ADnez-07a5b6395/" class="card-link"
                target="_blank">
                <img :src="linkedinIcon" alt="Icono de linkedin">
                <p class="txt-link">LinkedIn</p>
            </a>
            <a href="https://github.com/Obed-Is" class="card-link" target="_blank">
                <img :src="githubIcon" alt="Icono de github">
                <p class="txt-link">GitHub</p>
            </a>
            <a :href="gmailLink" class="card-link" target="_blank">
                <img :src="gmailIcon" alt="Icono de gmail">
                <p class="txt-link">Correo electrónico</p>
            </a>
        </div>
    </section>
</template>
<style scoped>
#contacto {
    width: 90%;
    min-height: 350px;
    margin-top: 80px;
    color: var(--color-primary);
}

h2 {
    align-self: flex-start;
    font-size: 1.9em;
    margin-bottom: 5px;
    color: var(--color-primary);
}

.txt-info {
    font-size: 1.2em;
    color: var(--color-third);
    margin-bottom: 25px;
}

.container-contact {
    width: 100%;
    height: auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
}

.card-link {
    width: 100%;
    height: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    gap: 10px;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.0));
    border: 1px solid var(--card-color-border);
    border-radius: var(--card-radius-border);
    transition: all .3s ease;

    &:hover {
        background: var(--background-gradient);
        box-shadow: var(--box-shadow-secondary);
    }
}

.card-link img {
    width: 33px;
    height: 33px;
}

.card-link .txt-link {
    font-size: 1.2em;
    color: var(--color-primary);
}
</style>