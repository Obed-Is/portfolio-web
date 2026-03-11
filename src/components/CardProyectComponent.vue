<script setup>
defineProps({
    urlGitHub: {
        type: String,
        required: true
    },
    fotoProyecto: {
        type: String,
        required: true
    },
    altProyecto: {
        type: String,
        required: true
    },
    titulo: {
        type: String,
        required: true
    },
    descripcion: {
        type: String,
        required: true
    },
    deploy: {
        type: String,
        required: false
    },

})
</script>

<template>
    <!-- urlGithub -->
    <a :href="urlGitHub" target="_blank" class="card">
        <div class="media">
            <!-- fotoProyecto, altProyecto -->
            <img :src="fotoProyecto" :alt="altProyecto" loading="lazy" />
        </div>

        <div class="info">
            <section>
                <!-- titulo -->
                <h3>{{ titulo }}</h3>
                <!-- descripcion -->
                <p class="txt-info">{{ descripcion }}</p>
            </section>

            <!-- deploy -->
            <a v-if="deploy" :href="deploy" target="_blank" class="deploy">Abrir proyecto en línea</a>

            <!-- tecnologias -->
            <div class="badges">
                <!-- icono, tituloIcono, altIcono -->
                <slot />
            </div>
        </div>
    </a>
</template>

<style scoped>
.card {
    display: flex;
    align-items: stretch;
    gap: 18px;
    padding: 12px;
    border-radius: var(--card-radius-border);
    background: var(--background-gradient);
    border: 1px solid var(--card-color-border);
    box-shadow: 0 6px 18px rgba(8, 15, 30, 0.06);
    text-decoration: none;
    transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease;
    color: inherit;
}

.card:hover {
    box-shadow: var(--box-shadow-secondary);
    border-color: rgba(17, 82, 212, 0.16);
}

.media {
    flex: 0 0 400px;
    border-radius: calc(var(--card-radius-border) - 2px);
    overflow: hidden;
    background: linear-gradient(135deg, rgba(0, 0, 0, 0.03), rgba(0, 0, 0, 0.01));
}

.media img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transform: scale(1.05);
    transition: transform .6s ease;
}

.card:hover .media img {
    transform: scale(1);
}

.info {
    flex: 1 1 auto;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 8px;
    padding: 6px 4px;
}

h3 {
    margin: 0;
    font-size: 1.25rem;
    color: var(--color-primary);
}

.txt-info {
    margin: 6px 0 0 0;
    color: var(--color-third);
    font-size: 0.98rem;
    line-height: 1.45;
}

.badges {
    margin-top: 10px;
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
}

.deploy {
    width: fit-content;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 14px;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.1);
    color: var(--color-primary);
    font-size: 0.9rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    backdrop-filter: blur(8px);
    box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.deploy:hover {
    transform: translateY(-2px);
    border-color: var(--color-primary);
    background-color: rgba(255, 255, 255, 0.05);
    box-shadow: 0 4px 14px rgba(255, 255, 255, 0.08);
}


@media (max-width: 720px) {
    .card {
        flex-direction: column;
        gap: 12px;
    }

    .media {
        width: 100%;
        flex: none;
        height: 180px;
    }

    .media img {
        height: 100%;
    }
}
</style>