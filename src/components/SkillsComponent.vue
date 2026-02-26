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

import htmlIcon from '@/assets/svgTecnologias/html5.svg';
import cssIcon from '@/assets/svgTecnologias/css.svg';
import jsIcon from '@/assets/svgTecnologias/javascript.svg';
import vueIcon from '@/assets/svgTecnologias/vue.svg';

const backendSkills = [
    { name: 'Node.js', icon: nodeIcon, alt: 'Node.js Logo' },
    { name: 'Express.js', icon: expressIcon, alt: 'Express.js Logo' },
    { name: 'API REST', icon: apiRestIcon, alt: 'API REST Logo' },
    { name: 'JWT', icon: jwtIcon, alt: 'JWT Logo' },
    { name: 'MySQL', icon: mysqlIcon, alt: 'MySQL Logo' },
    { name: 'Postman', icon: postmanIcon, alt: 'Postman Logo' },
    { name: 'Git', icon: gitIcon, alt: 'Git Logo' },
    { name: 'Docker', icon: dockerIcon, alt: 'Docker Logo' },
];

const frontendSkills = [
    { name: 'HTML5', icon: htmlIcon, alt: 'HTML5 Logo' },
    { name: 'CSS3', icon: cssIcon, alt: 'CSS3 Logo' },
    { name: 'JavaScript', icon: jsIcon, alt: 'JavaScript Logo' },
    { name: 'Vue.js', icon: vueIcon, alt: 'Vue.js Logo' },
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
        { threshold: 0.15 }
    );

    const section = document.getElementById('habilidades');
    if (section) observer.observe(section);
});
</script>

<template>
    <section id="habilidades" :class="{ 'animate-in': isVisible }">
        <h2>Habilidades</h2>

        <!-- Backend — principal -->
        <div class="skill-group backend-group">
            <div class="group-header">
                <span class="group-badge">★</span>
                <span class="group-label">Backend</span>
                <span class="group-tag">Enfoque principal</span>
                <span class="group-line"></span>
            </div>
            <div class="skills-grid skills-grid--backend">
                <div v-for="(tech, i) in backendSkills" :key="tech.name" class="skill-card skill-card--backend"
                    :style="{ '--delay': i * 0.1 + 's' }">
                    <div class="icon-wrapper">
                        <img :src="tech.icon" :alt="tech.alt" class="skill-icon" />
                    </div>
                    <span class="skill-name">{{ tech.name }}</span>
                </div>
            </div>
        </div>

        <!-- Frontend — complementario -->
        <div class="skill-group frontend-group">
            <div class="group-header">
                <span class="group-label group-label--secondary">Frontend</span>
                <span class="group-tag group-tag--secondary">Complementario</span>
                <span class="group-line group-line--secondary"></span>
            </div>
            <div class="skills-grid skills-grid--frontend">
                <div v-for="(tech, i) in frontendSkills" :key="tech.name" class="skill-card skill-card--frontend"
                    :style="{ '--delay': (i * 0.1 + 0.7) + 's' }">
                    <div class="icon-wrapper">
                        <img :src="tech.icon" :alt="tech.alt" class="skill-icon" />
                    </div>
                    <span class="skill-name">{{ tech.name }}</span>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
section {
    display: flex;
    flex-direction: column;
    width: 90%;
    margin: 60px 0;
    gap: 45px;
}

h2 {
    align-self: flex-start;
    font-size: 1.9em;
    margin-bottom: 0;
    color: var(--color-primary);
    font-weight: 700;
}

.skill-group {
    display: flex;
    flex-direction: column;
    gap: 22px;
}

.backend-group {
    padding: 28px;
    border-radius: var(--card-radius-border);
    border: 1px solid rgba(76, 99, 232, 0.2);
    background: linear-gradient(160deg, rgba(76, 99, 232, 0.06) 0%, transparent 60%);
    position: relative;
}

.frontend-group {
    padding: 0 4px;
    opacity: 0.85;
}

.group-header {
    display: flex;
    align-items: center;
    gap: 10px;
}

.group-badge {
    font-size: 1em;
    color: var(--color-secondary);
    animation: pulse 2s ease-in-out infinite;
}

.group-label {
    font-size: 1.25em;
    font-weight: 700;
    color: var(--color-secondary);
    white-space: nowrap;
    letter-spacing: 0.5px;
}

.group-label--secondary {
    font-size: 1.05em;
    font-weight: 600;
    color: var(--color-third);
}

.group-tag {
    font-size: 0.7em;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: var(--color-secondary);
    background: rgba(76, 99, 232, 0.12);
    padding: 3px 10px;
    border-radius: 20px;
    white-space: nowrap;
}

.group-tag--secondary {
    color: var(--color-third);
    background: rgba(146, 161, 182, 0.1);
}

.group-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--color-secondary), transparent);
}

.group-line--secondary {
    background: linear-gradient(90deg, rgba(146, 161, 182, 0.4), transparent);
}

.skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.skills-grid--backend {
    justify-content: flex-start;
}

.skills-grid--frontend {
    justify-content: flex-start;
}

.skill-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid var(--card-color-border);
    border-radius: var(--card-radius-border);
    transition: transform 0.35s ease, box-shadow 0.35s ease, border-color 0.35s ease;
    cursor: default;
    opacity: 0;
    transform: translateY(25px);
}

section.animate-in .skill-card {
    animation: fadeSlideUp 0.5s ease forwards;
    animation-delay: var(--delay);
}

.skill-card--backend {
    width: 130px;
    height: 130px;
    padding: 22px;
    background: linear-gradient(145deg, rgba(76, 99, 232, 0.1), rgba(76, 99, 232, 0.02));
    border-color: rgba(76, 99, 232, 0.25);
}

.skill-card--backend:hover {
    transform: translateY(-6px) scale(1.05);
    box-shadow: 0 8px 28px rgba(76, 99, 232, 0.35);
    border-color: var(--color-secondary);
}

.skill-card--frontend {
    width: 95px;
    height: 95px;
    padding: 16px;
    background: rgba(255, 255, 255, 0.02);
    border-color: rgba(255, 255, 255, 0.06);
}

.skill-card--frontend:hover {
    transform: translateY(-4px);
    box-shadow: var(--box-shadow-secondary);
    border-color: var(--color-third);
}

.icon-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 8px;
}

.skill-card--backend .skill-icon {
    width: 50px;
    height: 50px;
    object-fit: contain;
    filter: drop-shadow(0 0 6px rgba(76, 99, 232, 0.35));
    transition: filter 0.3s ease;
}

.skill-card--backend:hover .skill-icon {
    filter: drop-shadow(0 0 12px rgba(76, 99, 232, 0.6));
}

.skill-card--frontend .skill-icon {
    width: 35px;
    height: 35px;
    object-fit: contain;
    opacity: 0.8;
    transition: filter 0.3s ease, opacity 0.3s ease;
}

.skill-card--frontend:hover .skill-icon {
    opacity: 1;
    filter: drop-shadow(0 0 6px rgba(146, 161, 182, 0.4));
}

.skill-name {
    color: var(--color-primary);
    font-size: 0.85em;
    font-weight: 500;
    text-align: center;
}

.skill-card--backend .skill-name {
    font-size: 0.9em;
    font-weight: 600;
}

.skill-card--frontend .skill-name {
    font-size: 0.75em;
    color: var(--color-third);
}

@keyframes fadeSlideUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes pulse {

    0%,
    100% {
        opacity: 1;
    }

    50% {
        opacity: 0.5;
    }
}

@media (max-width: 768px) {
    section {
        width: 90%;
        margin: 40px 0;
        gap: 30px;
    }

    .backend-group {
        padding: 18px;
    }

    .skills-grid {
        gap: 12px;
        justify-content: center;
    }

    .skill-card--backend {
        width: 105px;
        height: 105px;
        padding: 16px;
    }

    .skill-card--backend .skill-icon {
        width: 42px;
        height: 42px;
    }

    .skill-card--frontend {
        width: 82px;
        height: 82px;
        padding: 12px;
    }

    .skill-card--frontend .skill-icon {
        width: 30px;
        height: 30px;
    }

    .skill-name {
        font-size: 0.7em;
    }

    .group-tag {
        font-size: 0.6em;
        padding: 2px 7px;
    }
}
</style>
