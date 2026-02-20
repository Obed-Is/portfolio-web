<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);
const activeSection = ref('inicio');
const menuOpen = ref(false);

const sections = ['inicio', 'proyectos', 'habilidades', 'contacto'];

const handleScroll = () => {
    isScrolled.value = window.scrollY >= 50;

    const scrollPos = window.scrollY + 120;
    for (let i = sections.length - 1; i >= 0; i--) {
        const el = document.getElementById(sections[i]);
        if (el && el.offsetTop <= scrollPos) {
            activeSection.value = sections[i];
            break;
        }
    }
};

const toggleMenu = () => {
    menuOpen.value = !menuOpen.value;
};

const closeMenu = () => {
    menuOpen.value = false;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll();
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});

const navLinks = [
    { id: 'inicio', label: 'Inicio' },
    { id: 'proyectos', label: 'Proyectos' },
    { id: 'habilidades', label: 'Habilidades' },
    { id: 'contacto', label: 'Contacto' },
];
</script>

<template>
    <nav :class="{ scrolled: isScrolled }">
        <div class="nav-inner">
            <a href="#inicio" class="nav-logo" @click="closeMenu">OA<span class="logo-dot">.</span></a>

            <button class="hamburger" :class="{ open: menuOpen }" @click="toggleMenu" aria-label="Menu">
                <span></span>
                <span></span>
                <span></span>
            </button>

            <ul :class="{ show: menuOpen }">
                <li v-for="link in navLinks" :key="link.id">
                    <a :href="'#' + link.id" :class="{ active: activeSection === link.id }" @click="closeMenu">
                        {{ link.label }}
                    </a>
                </li>
            </ul>
        </div>
    </nav>

    <div v-if="menuOpen" class="nav-overlay" @click="closeMenu"></div>
</template>

<style scoped>
nav {
    position: fixed;
    top: 16px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 100;
    padding: 0;
    border-radius: 50px;
    border: 1px solid transparent;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

nav.scrolled {
    background: rgba(10, 15, 29, 0.75);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border-color: var(--card-color-border);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.nav-inner {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 10px 8px 20px;
}

.nav-logo {
    font-size: 1.3em;
    font-weight: 800;
    color: var(--color-primary);
    text-decoration: none;
    letter-spacing: -0.5px;
    margin-right: 16px;
    transition: color 0.3s ease;
}

.logo-dot {
    color: var(--color-secondary);
}

.nav-logo:hover {
    color: var(--color-secondary);
}

ul {
    display: flex;
    gap: 4px;
    list-style: none;
    margin: 0;
    padding: 0;
}

li a {
    position: relative;
    color: var(--color-third);
    font-size: 0.92em;
    font-weight: 500;
    padding: 8px 16px;
    border-radius: 30px;
    transition: color 0.25s ease, background-color 0.25s ease;
    text-decoration: none;
    white-space: nowrap;
}

li a:hover {
    color: var(--color-primary);
    background-color: rgba(255, 255, 255, 0.06);
}

li a.active {
    color: var(--color-primary);
    background-color: rgba(76, 99, 232, 0.15);
    font-weight: 600;
}

.hamburger {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    width: 32px;
    height: 32px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 4px;
    z-index: 110;
}

.hamburger span {
    display: block;
    width: 100%;
    height: 2px;
    background: var(--color-primary);
    border-radius: 2px;
    transition: all 0.3s ease;
    transform-origin: center;
}

.hamburger.open span:nth-child(1) {
    transform: translateY(7px) rotate(45deg);
}

.hamburger.open span:nth-child(2) {
    opacity: 0;
}

.hamburger.open span:nth-child(3) {
    transform: translateY(-7px) rotate(-45deg);
}

.nav-overlay {
    display: none;
}

@media (max-width: 768px) {
    nav {
        top: 12px;
        left: 16px;
        right: 16px;
        transform: none;
        border-radius: var(--card-radius-border);
    }

    nav.scrolled {
        background: rgba(10, 15, 29, 0.9);
    }

    .nav-inner {
        justify-content: space-between;
        padding: 10px 16px;
    }

    .nav-logo {
        margin-right: 0;
    }

    .hamburger {
        display: flex;
    }

    ul {
        position: fixed;
        top: 0;
        right: 0;
        width: 260px;
        height: 100dvh;
        flex-direction: column;
        gap: 0;
        padding: 80px 24px 24px;
        background: rgba(10, 15, 29, 0.95);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border-left: 1px solid var(--card-color-border);
        transform: translateX(100%);
        transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
        z-index: 105;
    }

    ul.show {
        transform: translateX(0);
    }

    li a {
        display: block;
        font-size: 1.1em;
        padding: 14px 18px;
        border-radius: var(--card-radius-border);
    }

    li a.active {
        background-color: rgba(76, 99, 232, 0.15);
    }

    .nav-overlay {
        display: block;
        position: fixed;
        inset: 0;
        background: rgba(0, 0, 0, 0.5);
        z-index: 99;
    }
}
</style>