<script setup>
defineProps({
  urlIcon: {
    type: String,
    required: true
  },
  altIcon: {
    type: String,
    default: ''
  },
  titleBadge: {
    type: String,
    required: true
  }
})
</script>
<template>
    <span class="badge">
        <img :src="urlIcon" :alt="altIcon" />
        <span>{{ titleBadge }}</span>
    </span>
</template>

<style scoped>
.badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 4px 10px;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.08);
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--color-third);
    transition: all 0.3s ease;
}

.badge:hover {
    background: rgba(76, 99, 232, 0.1);
    border-color: rgba(76, 99, 232, 0.3);
    color: var(--color-primary);
}

.badge img {
    width: 18px;
    height: 18px;
    display: block;
}
</style>