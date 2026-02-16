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
    gap: 8px;
    padding: 6px 10px;
    border-radius: var(--card-radius-border);
    background: rgba(17, 82, 212, 0.05);
    border: 1px solid rgba(17, 82, 212, 0.06);
    font-size: 0.9rem;
    color: var(--color-primary);
}

.badge img {
    width: 18px;
    height: 18px;
    display: block;
}
</style>