<template>
    <footer>
        <div class="footer-divider"></div>
        <p class="footer-copy">
            <span class="footer-logo">OA<span class="dot">.</span></span>
            {{ new Date().getFullYear() }} Obed Aquino.
        </p>
    </footer>
</template>

<style scoped>
footer {
    width: 90%;
    padding: 30px 0 24px;
    margin-top: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 18px;
}

.footer-logo {
    font-size: 1.3em;
    font-weight: 800;
    color: var(--color-primary);
    letter-spacing: -0.5px;
}

.dot {
    color: var(--color-secondary);
}

.footer-divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--card-color-border), transparent);
}

.footer-copy {
    font-size: 0.9em;
    color: var(--color-third);
}

@media (max-width: 600px) {
    footer {
        width: 100%;
        margin-top: 20px;
    }
}
</style>
