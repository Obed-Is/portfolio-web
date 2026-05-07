<script setup>
import { ref, onMounted } from 'vue';

import nodeIcon from '@/assets/svgTecnologias/nodejs.svg';
import expressIcon from '@/assets/svgTecnologias/expressjs.svg';
import mysqlIcon from '@/assets/svgTecnologias/mysql-wordmark-dark.svg';
import jwtIcon from '@/assets/svgTecnologias/jwt.svg';
import postmanIcon from '@/assets/svgTecnologias/postman.svg';
import apiRestIcon from '@/assets/svgTecnologias/apirest.svg';
import gitIcon from '@/assets/svgTecnologias/git.svg';
import dockerIcon from '@/assets/svgTecnologias/docker.svg';
import phpIcon from '@/assets/svgTecnologias/php.svg';
import sqlServerIcon from '@/assets/svgTecnologias/sql-server.svg';
import csharpIcon from '@/assets/svgTecnologias/csharp.svg';
import dotnetIcon from '@/assets/svgTecnologias/dotnet.svg';

import htmlIcon from '@/assets/svgTecnologias/html5.svg';
import cssIcon from '@/assets/svgTecnologias/css.svg';
import jsIcon from '@/assets/svgTecnologias/javascript.svg';
import vueIcon from '@/assets/svgTecnologias/vue.svg';

const skills = [
    { name: 'HTML5', icon: htmlIcon, alt: 'HTML5 Logo' },
    { name: 'CSS3', icon: cssIcon, alt: 'CSS3 Logo' },
    { name: 'JavaScript', icon: jsIcon, alt: 'JavaScript Logo' },
    { name: 'Vue.js', icon: vueIcon, alt: 'Vue.js Logo' },
    { name: 'Node.js', icon: nodeIcon, alt: 'Node.js Logo' },
    { name: 'CSharp', icon: csharpIcon, alt: 'CSharp Logo' },
    { name: 'Dotnet', icon: dotnetIcon, alt: 'Dotnet Logo' },
    { name: 'Express.js', icon: expressIcon, alt: 'Express.js Logo' },
    { name: 'API REST', icon: apiRestIcon, alt: 'API REST Logo' },
    { name: 'JWT', icon: jwtIcon, alt: 'JWT Logo' },
    { name: 'MySQL', icon: mysqlIcon, alt: 'MySQL Logo' },
    { name: 'SQL Server', icon: sqlServerIcon, alt: 'SQL Server Logo' },
    { name: 'Postman', icon: postmanIcon, alt: 'Postman Logo' },
    { name: 'Git', icon: gitIcon, alt: 'Git Logo' },
    { name: 'Docker', icon: dockerIcon, alt: 'Docker Logo' },
];

const isVisible = ref(false);

onMounted(() => {
    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    isVisible.value = true;
                    observer.unobserve(entry.target);
                }
            });
        },
        { threshold: 0.1 }
    );

    const section = document.getElementById('habilidades');
    if (section) observer.observe(section);
});
</script>

<template>
    <section id="habilidades" :class="{ 'animate-in': isVisible }">
        <div class="header-container">
            <h2 class="section-title">Habilidades</h2>
            <p class="section-subtitle">Tecnologías y herramientas que utilizo para dar vida a mis proyectos.</p>
        </div>

        <div class="skills-grid">
            <div v-for="(tech, i) in skills" :key="tech.name" class="skill-card" :style="{ '--delay': i * 0.05 + 's' }">
                <div class="card-glass"></div>
                <div class="icon-container">
                    <img :src="tech.icon" :alt="tech.alt" class="skill-icon" />
                </div>
                <span class="skill-name">{{ tech.name }}</span>
            </div>
        </div>
    </section>
</template>

<style scoped>
section {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 1200px;
    margin: 100px auto;
    padding: 0 20px;
    gap: 60px;
}

.header-container {
    text-align: left;
    margin-bottom: 20px;
}

.section-title {
    font-size: 2.5rem;
    font-weight: 800;
    color: var(--color-primary);
    margin-bottom: 12px;
    letter-spacing: -0.02em;
}

.section-subtitle {
    font-size: 1.1rem;
    color: var(--color-third);
    max-width: 600px;
    line-height: 1.6;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 20px;
}

.skill-card {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 24px;
    height: 140px;
    border-radius: 20px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    opacity: 0;
    transform: translateY(30px);
}

section.animate-in .skill-card {
    animation: reveal 0.6s cubic-bezier(0.23, 1, 0.32, 1) forwards;
    animation-delay: var(--delay);
}

.card-glass {
    position: absolute;
    inset: 0;
    background: rgba(255, 255, 255, 0.03);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 20px;
    z-index: 0;
    transition: all 0.3s ease;
}

.skill-card:hover {
    transform: translateY(-8px) scale(1.05);
}

.skill-card:hover .card-glass {
    background: rgba(255, 255, 255, 0.06);
    border-color: rgba(76, 99, 232, 0.4);
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4),
        0 0 20px rgba(76, 99, 232, 0.1);
}

.icon-container {
    position: relative;
    z-index: 1;
    width: 48px;
    height: 48px;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.3s ease;
}

.skill-card:hover .icon-container {
    transform: scale(1.1);
}

.skill-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
    filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.2));
}

.skill-name {
    position: relative;
    z-index: 1;
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--color-primary);
    opacity: 0.8;
    transition: opacity 0.3s ease;
}

.skill-card:hover .skill-name {
    opacity: 1;
}

@keyframes reveal {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 768px) {
    section {
        margin: 60px auto;
        gap: 40px;
    }

    .section-title {
        font-size: 2rem;
    }

    .skills-grid {
        grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
        gap: 12px;
    }

    .skill-card {
        height: 110px;
        padding: 16px;
    }

    .icon-container {
        width: 36px;
        height: 36px;
    }

    .skill-name {
        font-size: 0.8rem;
    }
}
</style>
