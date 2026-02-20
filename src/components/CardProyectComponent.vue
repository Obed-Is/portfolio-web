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