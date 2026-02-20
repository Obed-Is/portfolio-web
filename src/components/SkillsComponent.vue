<script setup>
import { ref, onMounted } from 'vue';

import nodeIcon from '@/assets/svgtecnologias/nodejs.svg';
import expressIcon from '@/assets/svgtecnologias/expressjs.svg';
import mysqlIcon from '@/assets/svgtecnologias/mysql-wordmark-dark.svg';
import jwtIcon from '@/assets/svgtecnologias/jwt.svg';
import stripeIcon from '@/assets/svgtecnologias/stripe.svg';
import postmanIcon from '@/assets/svgtecnologias/postman.svg';
import apiRestIcon from '@/assets/svgtecnologias/apirest.svg';

import htmlIcon from '@/assets/svgtecnologias/html5.svg';
import cssIcon from '@/assets/svgtecnologias/css.svg';
import jsIcon from '@/assets/svgtecnologias/javascript.svg';
import vueIcon from '@/assets/svgtecnologias/vue.svg';

const backendSkills = [
    { name: 'Node.js', icon: nodeIcon, alt: 'Node.js Logo' },
    { name: 'Express.js', icon: expressIcon, alt: 'Express.js Logo' },
    { name: 'MySQL', icon: mysqlIcon, alt: 'MySQL Logo' },
    { name: 'JWT', icon: jwtIcon, alt: 'JWT Logo' },
    { name: 'Stripe', icon: stripeIcon, alt: 'Stripe Logo' },
    { name: 'Postman', icon: postmanIcon, alt: 'Postman Logo' },
    { name: 'API REST', icon: apiRestIcon, alt: 'API REST Logo' },
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

        <!-- Backend -->
        <div class="skill-group backend-group">
            <div class="group-header">
                <span class="group-label">Backend</span>
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

        <!-- Frontend -->
        <div class="skill-group frontend-group">
            <div class="group-header">
                <span class="group-label">Frontend</span>
                <span class="group-line"></span>
            </div>
            <div class="skills-grid skills-grid--frontend">
                <div v-for="(tech, i) in frontendSkills" :key="tech.name" class="skill-card skill-card--frontend"
                    :style="{ '--delay': (i * 0.1 + 0.6) + 's' }">
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
    gap: 40px;
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
    gap: 20px;
}

.group-header {
    display: flex;
    align-items: center;
    gap: 14px;
}

.group-label {
    font-size: 1.15em;
    font-weight: 600;
    color: var(--color-secondary);
    white-space: nowrap;
    letter-spacing: 0.5px;
}

.group-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--color-secondary), transparent);
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
    background: linear-gradient(145deg, rgba(76, 99, 232, 0.08), rgba(76, 99, 232, 0.02));
    border-color: rgba(76, 99, 232, 0.25);
}

.skill-card--backend:hover {
    transform: translateY(-6px) scale(1.04);
    box-shadow: var(--box-shadow-secondary);
    border-color: var(--color-secondary);
}

.skill-card--frontend {
    width: 105px;
    height: 105px;
    padding: 18px;
    background: rgba(255, 255, 255, 0.03);
}

.skill-card--frontend:hover {
    transform: translateY(-5px);
    box-shadow: var(--box-shadow-secondary);
    border-color: var(--color-secondary);
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
    filter: drop-shadow(0 0 10px rgba(76, 99, 232, 0.55));
}

.skill-card--frontend .skill-icon {
    width: 40px;
    height: 40px;
    object-fit: contain;
    transition: filter 0.3s ease;
}

.skill-card--frontend:hover .skill-icon {
    filter: drop-shadow(0 0 8px rgba(76, 99, 232, 0.4));
}

.skill-name {
    color: var(--color-primary);
    font-size: 0.85em;
    font-weight: 500;
    text-align: center;
}

.skill-card--backend .skill-name {
    font-size: 0.9em;
}

@keyframes fadeSlideUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 768px) {
    section {
        width: 90%;
        margin: 40px 0;
        gap: 30px;
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
        width: 90px;
        height: 90px;
        padding: 14px;
    }

    .skill-card--frontend .skill-icon {
        width: 34px;
        height: 34px;
    }

    .skill-name {
        font-size: 0.75em;
    }
}
</style>
