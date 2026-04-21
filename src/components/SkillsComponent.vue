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

const backendSkills = [
    { name: 'Node.js', icon: nodeIcon, alt: 'Node.js Logo' },
    { name: 'CSharp', icon: csharpIcon, alt: 'CSharop.js Logo' },
    { name: 'Dotnet', icon: dotnetIcon, alt: 'Dotnet.js Logo' },
    { name: 'Express.js', icon: expressIcon, alt: 'Express.js Logo' },
    { name: 'API REST', icon: apiRestIcon, alt: 'API REST Logo' },
    { name: 'JWT', icon: jwtIcon, alt: 'JWT Logo' },
    { name: 'MySQL', icon: mysqlIcon, alt: 'MySQL Logo' },
    { name: 'SQL Server', icon: sqlServerIcon, alt: 'SQL Server Logo' },
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

// todas las tecnologias en una sola lista
const skills = [...backendSkills, ...frontendSkills];

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

        <div class="skill-group unified-group">
            <div class="group-header">
                <span class="group-label">Tecnologías</span>
                <span class="group-line"></span>
            </div>

            <div class="skills-grid skills-grid--all">
                <div v-for="(tech, i) in skills" :key="tech.name" class="skill-card skill-card--unified"
                    :style="{ '--delay': i * 0.08 + 's' }">
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

.group-header {
    display: flex;
    align-items: center;
    gap: 10px;
}

.group-label {
    font-size: 1.15em;
    font-weight: 700;
    color: var(--color-secondary);
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

.group-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--color-secondary), transparent);
}

.skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 18px;
}

.skills-grid--all {
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
    transform: translateY(20px);
}

section.animate-in .skill-card {
    animation: fadeSlideUp 0.45s ease forwards;
    animation-delay: var(--delay);
}

.skill-card--unified {
    width: 120px;
    height: 120px;
    padding: 18px;
    background: linear-gradient(145deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-color: rgba(255,255,255,0.06);
}

.skill-card--unified:hover {
    transform: translateY(-6px) scale(1.04);
    box-shadow: 0 10px 30px rgba(0,0,0,0.12);
    border-color: var(--color-secondary);
}

.icon-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 8px;
}

.skill-icon {
    width: 44px;
    height: 44px;
    object-fit: contain;
    transition: filter 0.3s ease, opacity 0.3s ease;
}

.skill-card--unified:hover .skill-icon {
    filter: drop-shadow(0 0 10px rgba(76, 99, 232, 0.25));
}

.skill-name {
    color: var(--color-primary);
    font-size: 0.85em;
    font-weight: 600;
    text-align: center;
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

    .skill-card--unified {
        width: 92px;
        height: 92px;
        padding: 12px;
    }

    .skill-icon {
        width: 32px;
        height: 32px;
    }

    .skill-name {
        font-size: 0.72em;
    }

    .group-tag {
        font-size: 0.6em;
        padding: 2px 7px;
    }
}
</style>
