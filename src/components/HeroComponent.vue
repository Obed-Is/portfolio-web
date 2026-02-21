<script setup>
import { ref, onMounted } from 'vue';
import fotoPerfil from '@/assets/foto-perfil.webp';

const loaded = ref(false);

onMounted(() => {
    requestAnimationFrame(() => {
        loaded.value = true;
    });
});
</script>

<template>
    <section class="first-section" :class="{ 'hero-loaded': loaded }">
        <div class="info-section">
            <p class="txt-name anim-item" style="--i: 0">
                <span class="txt-var">{</span> Hola soy, Obed Aquino <span class="txt-var">}</span>
            </p>
            <h1 class="anim-item" style="--i: 1">
                Desarrollador
                <span class="letter-tag">
                    &lt; Full Stack Jr /&gt;
                </span>
            </h1>
            <p class="txt-info anim-item" style="--i: 2">
                Desarrollo APIs y aplicaciones web con Node.js y Express. Me enfoco en construir servicios backend
                seguros, escalables y bien estructurados, trabajando con bases de datos SQL y autenticación con JWT.
            </p>
            <div class="btn-group anim-item" style="--i: 3">
                <a href="#contacto" class="btn btn-primary">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                        stroke-linecap="round" stroke-linejoin="round">
                        <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" />
                        <polyline points="22,6 12,13 2,6" />
                    </svg>
                    Contacto
                </a>
                <a href="/CV_Obed_Aquino_Desarrollador_Full_Stack_Junior.pdf" download="CV_Obed_Aquino.pdf"
                    class="btn btn-secondary">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                        stroke-linecap="round" stroke-linejoin="round">
                        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
                        <polyline points="7 10 12 15 17 10" />
                        <line x1="12" y1="15" x2="12" y2="3" />
                    </svg>
                    Descargar CV
                </a>
            </div>
        </div>
        <div class="perfil-section anim-item" style="--i: 1">
            <div class="perfil-ring">
                <img :src="fotoPerfil" alt="Foto de perfil" class="ft-perfil">
            </div>
            <div class="status-badge">
                <span class="status-dot"></span>
                Disponible para trabajar
            </div>
        </div>
    </section>
</template>

<style scoped>
.first-section {
    width: 90%;
    display: grid;
    grid-template-columns: 1.8fr 1fr;
    align-items: center;
    justify-items: center;
    margin-top: 80px;
    padding: 40px 52px;
    background: var(--background-gradient);
    border: 1px solid var(--card-color-border);
    border-radius: var(--card-radius-border);
    transition: border-color 0.5s ease, box-shadow 0.5s ease;
    position: relative;
    overflow: hidden;
}

.first-section::before {
    content: '';
    position: absolute;
    top: -50%;
    right: -20%;
    width: 400px;
    height: 400px;
    background: radial-gradient(circle, rgba(76, 99, 232, 0.08) 0%, transparent 70%);
    pointer-events: none;
}

.first-section:hover {
    border-color: rgba(76, 99, 232, 0.3);
    box-shadow: var(--box-shadow-secondary);
}

.anim-item {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
    transition-delay: calc(var(--i) * 0.15s);
}

.hero-loaded .anim-item {
    opacity: 1;
    transform: translateY(0);
}

.info-section {
    align-self: center;
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.txt-name {
    font-size: 1.4em;
    font-weight: 600;
    color: var(--color-primary);
}

.txt-var {
    background-color: var(--card-color-border);
    color: var(--color-third);
    font-weight: 700;
    padding: 4px 10px;
    border-radius: var(--card-radius-border);
    font-family: 'Courier New', monospace;
}

h1 {
    font-size: 2.5em;
    line-height: 1.15;
    color: var(--color-primary);
}

.letter-tag {
    color: var(--color-secondary);
    font-weight: 800;
    position: relative;
}

.txt-info {
    color: var(--color-third);
    font-size: 1.2em;
    line-height: 1.6;
    max-width: 520px;
}

.btn-group {
    display: flex;
    gap: 14px;
    margin-top: 6px;
}

.btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    line-height: 1;
    padding: 12px 22px;
    font-size: 0.95em;
    font-weight: 600;
    cursor: pointer;
    border-radius: 50px;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    text-decoration: none;
    color: var(--color-primary);
}

.btn-primary {
    background-color: var(--color-secondary);
    border: 1px solid var(--color-secondary);
}

.btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(76, 99, 232, 0.4);
    background-color: #5a73f0;
}

.btn-secondary {
    background-color: transparent;
    border: 1px solid rgba(241, 245, 249, 0.3);
}

.btn-secondary:hover {
    transform: translateY(-2px);
    border-color: var(--color-primary);
    background-color: rgba(255, 255, 255, 0.05);
    box-shadow: 0 4px 14px rgba(255, 255, 255, 0.08);
}

.perfil-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}

.perfil-ring {
    position: relative;
    padding: 4px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--color-secondary), rgba(76, 99, 232, 0.3), var(--card-color-border));
    transition: all 0.4s ease;
}

.perfil-ring:hover {
    box-shadow: 0 0 30px rgba(76, 99, 232, 0.3);
}

.ft-perfil {
    display: block;
    max-width: 280px;
    width: 100%;
    object-fit: cover;
    border-radius: 50%;
    border: 4px solid var(--background);
    transition: transform 0.4s ease;
}

.perfil-ring:hover .ft-perfil {
    transform: scale(1.02);
}

.status-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 6px 16px;
    border-radius: 30px;
    font-size: 0.82em;
    font-weight: 500;
    color: #6ee7b7;
    background: rgba(110, 231, 183, 0.08);
    border: 1px solid rgba(110, 231, 183, 0.2);
}

.status-dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: #6ee7b7;
    animation: blink 2s ease-in-out infinite;
}

@keyframes blink {

    0%,
    100% {
        opacity: 1;
    }

    50% {
        opacity: 0.3;
    }
}

@media (max-width: 1150px) {
    h1 {
        display: flex;
        flex-direction: column;
    }

    .txt-info {
        max-width: 90%;
        font-size: 1em;
    }

    .ft-perfil {
        max-width: 240px;
    }
}

@media (max-width: 820px) {
    .first-section {
        margin-top: 80px;
        display: flex;
        flex-direction: column;
        gap: 30px;
        padding: 30px 24px;
    }

    .txt-name {
        font-size: 1.2em;
    }

    .info-section {
        order: 2;
        text-align: center;
        align-items: center;

        h1 {
            font-size: 1.9em;
        }
    }

    .txt-info {
        max-width: 95%;
        font-size: 1.1em !important;
        text-align: center;
    }

    .perfil-section {
        order: 1;
    }

    .ft-perfil {
        max-width: 200px;
    }

    .btn-group {
        flex-direction: column;
        width: 100%;
        align-items: center;
    }

    .btn {
        justify-content: center;
        width: 100%;
        max-width: 260px;
        padding: 12px;
    }
}

@media (max-width: 460px) {
    .txt-name {
        font-size: 1em;
    }

    h1 {
        font-size: 1.6em !important;
    }

    .txt-info {
        font-size: 1em !important;
    }

    .btn {
        font-size: 0.9em;
    }

    .ft-perfil {
        max-width: 170px;
    }
}
</style>