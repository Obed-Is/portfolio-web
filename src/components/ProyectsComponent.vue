<script setup>
import CardProyectComponent from './CardProyectComponent.vue';
// sistema-inventario, Stripe y portafolio
import ftInventario from '@/assets/sistema-inventario.webp';
import ftPasarela from '@/assets/pasarela-stripe.webp';
import ftPortafolio from '@/assets/portafolio-web.webp';

import BadgeCardComponent from './BadgeCardComponent.vue';
import nodeIcon from '@/assets/svgTecnologias/nodejs.svg'
import jwtIcon from '@/assets/svgTecnologias/jwt.svg'
import expressIcon from '@/assets/svgTecnologias/expressjs.svg'
import mysqlIcon from '@/assets/svgTecnologias/mysql-wordmark-dark.svg'
import vueIcon from '@/assets/svgTecnologias/vue.svg'
import jsIcon from '@/assets/svgTecnologias/javascript.svg'
import gitHubIcon from '@/assets/svgTecnologias/github_dark.svg'
import stripe from '@/assets/svgTecnologias/stripe.svg'
import postman from '@/assets/svgTecnologias/postman.svg'
import html5 from '@/assets/svgTecnologias/html5.svg'
import css from '@/assets/svgTecnologias/css.svg'

</script>
<template>
    <section id="proyectos">
        <h2>Proyectos</h2>
        <div class="container-proyects">

            <!-- sistema de inventario y ventas -->
            <CardProyectComponent :urlGitHub="'https://github.com/Obed-Is/sistema-inventario'"
                :fotoProyecto="ftInventario" :altProyecto="'Foto del sistema de inventario'" ,
                :titulo="'Sistema de inventario y ventas'" :descripcion="`Orientado a pequeñas y medianas empresas, diseñado para facilitar y agilizar las
                operaciones diarias de gestión de productos y ventas, con control de usuarios y roles.`">

                <BadgeCardComponent :urlIcon="nodeIcon" :title-badge="'Node.js'" :alt-icon="'Icono de Node.js'" />
                <BadgeCardComponent :urlIcon="jwtIcon" :title-badge="'JWT'" :alt-icon="'Icono de JWT'" />
                <BadgeCardComponent :urlIcon="expressIcon" :title-badge="'Express.js'"
                    :alt-icon="'Icono de Express.js'" />
                <BadgeCardComponent :urlIcon="mysqlIcon" :title-badge="'MySql'" :alt-icon="'Icono de MySql'" />
                <BadgeCardComponent :urlIcon="vueIcon" :title-badge="'Vue.js'" :alt-icon="'Icono de Vue.js'" />
                <BadgeCardComponent :urlIcon="jsIcon" :title-badge="'Javascript.js'"
                    :alt-icon="'Icono de Javascript.js'" />
                <BadgeCardComponent :urlIcon="postman" :title-badge="'Postman'" :alt-icon="'Icono de Postman'" />
                <BadgeCardComponent :urlIcon="gitHubIcon" :title-badge="'GitHub'" :alt-icon="'Icono de GitHub'" />
            </CardProyectComponent> />

            <!-- Pasarela de pago con Api de Stripe -->
            <CardProyectComponent :urlGitHub="'https://github.com/Obed-Is/pasarela-pago-con-stripe-nodejs'"
                :fotoProyecto="ftPasarela" :altProyecto="'Foto de la pasarela de pago'" ,
                :titulo="'Pasarela de pago con Api de Stripe'" :descripcion="`Gestiona el ciclo completo de transacciones desde la 
                creacion y venta de productos hasta la verificacion de pagos mediante webhooks.`">

                <BadgeCardComponent :urlIcon="nodeIcon" :title-badge="'Node.js'" :alt-icon="'Icono de Node.js'" />
                <BadgeCardComponent :urlIcon="expressIcon" :title-badge="'Express.js'"
                    :alt-icon="'Icono de Express.js'" />
                <BadgeCardComponent :urlIcon="jsIcon" :title-badge="'Javascript.js'"
                    :alt-icon="'Icono de Javascript.js'" />
                <BadgeCardComponent :urlIcon="stripe" :title-badge="'Stripe'" :alt-icon="'Icono de Stripe'" />
                <BadgeCardComponent :urlIcon="gitHubIcon" :title-badge="'GitHub'" :alt-icon="'Icono de GitHub'" />
                <BadgeCardComponent :urlIcon="html5" :title-badge="'HTML'" :alt-icon="'Icono de html'" />
                <BadgeCardComponent :urlIcon="css" :title-badge="'CSS'" :alt-icon="'Icono de css'" />

            </CardProyectComponent> />

            <!-- portafolio(recordar actualizar si se cambia!!!!!) -->
            <CardProyectComponent :urlGitHub="'https://github.com/Obed-Is/portfolio-web'" :fotoProyecto="ftPortafolio"
                :altProyecto="'Foto del portafolio'" , :titulo="'Portafolio personal'" :descripcion="`Web personal con el objetivo de demostrar las habilidades
                y conocimientos adquiridos como desarrollador.`">
                <BadgeCardComponent :urlIcon="vueIcon" :title-badge="'Vue.js'" :alt-icon="'Icono de Vue.js'" />
                <BadgeCardComponent :urlIcon="nodeIcon" :title-badge="'Node.js'" :alt-icon="'Icono de Node.js'" />
                <BadgeCardComponent :urlIcon="jsIcon" :title-badge="'Javascript.js'"
                    :alt-icon="'Icono de Javascript.js'" />
                <BadgeCardComponent :urlIcon="gitHubIcon" :title-badge="'GitHub'" :alt-icon="'Icono de GitHub'" />
            </CardProyectComponent> />
        </div>
    </section>
</template>
<style scoped>
section {
    display: flex;
    flex-direction: column;
    width: 90%;
    margin: 60px 0;
    height: auto;
}

h2 {
    align-self: flex-start;
    font-size: 1.9em;
    margin-bottom: 25px;
    color: var(--color-primary);
}

.txt-git {
    padding: 5px 10px;
    background-color: var(--color-third);
    border-radius: var(--card-radius-border);
}
</style>