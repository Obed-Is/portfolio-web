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
    <div class="card">
        <div class="media">
            <img :src="fotoProyecto" :alt="altProyecto" loading="lazy" />
            <div class="overlay">
                <div class="links">
                    <a :href="urlGitHub" target="_blank" class="icon-link" title="Ver en GitHub">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
                    </a>
                    <a v-if="deploy" :href="deploy" target="_blank" class="icon-link" title="Ver demo">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
                    </a>
                </div>
            </div>
        </div>

        <div class="info">
            <div class="content">
                <h3>{{ titulo }}</h3>
                <p class="txt-info">{{ descripcion }}</p>
            </div>

            <div class="badges">
                <slot />
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    display: flex;
    flex-direction: column;
    height: 100%;
    border-radius: var(--card-radius-border);
    background: rgba(23, 27, 42, 0.4);
    backdrop-filter: blur(12px);
    border: 1px solid rgba(255, 255, 255, 0.05);
    overflow: hidden;
    transition: all 0.4s cubic-bezier(0.23, 1, 0.32, 1);
    position: relative;
}

.card:hover {
    transform: translateY(-8px);
    border-color: rgba(76, 99, 232, 0.4);
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4), 
                0 0 0 1px rgba(76, 99, 232, 0.2);
}

.card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at top right, rgba(76, 99, 232, 0.1), transparent);
    opacity: 0;
    transition: opacity 0.4s ease;
}

.card:hover::before {
    opacity: 1;
}

.media {
    position: relative;
    width: 100%;
    aspect-ratio: 16/9;
    overflow: hidden;
    background: #0d121f;
}

.media img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.8s cubic-bezier(0.2, 0, 0.2, 1);
}

.card:hover .media img {
    transform: scale(1.1);
}

.overlay {
    position: absolute;
    inset: 0;
    background: rgba(10, 15, 29, 0.6);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s ease;
    backdrop-filter: blur(4px);
}

.card:hover .overlay {
    opacity: 1;
}

.links {
    display: flex;
    gap: 15px;
}

.icon-link {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    background: var(--color-primary);
    color: var(--background);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    transform: translateY(20px);
}

.card:hover .icon-link {
    transform: translateY(0);
}

.icon-link:hover {
    transform: scale(1.1) !important;
    background: var(--color-secondary);
    color: white;
}

.info {
    padding: 20px;
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 15px;
    z-index: 1;
}

h3 {
    margin: 0;
    font-size: 1.25rem;
    color: var(--color-primary);
    font-weight: 700;
}

.txt-info {
    margin: 10px 0 0 0;
    color: var(--color-third);
    font-size: 0.92rem;
    line-height: 1.6;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.badges {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
}

@media (max-width: 720px) {
    .media {
        aspect-ratio: 16/10;
    }
}
</style>