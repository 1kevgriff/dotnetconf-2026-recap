<!-- Section divider. Navy ground, gold kicker. -->
<script setup lang="ts">
defineProps<{ kicker?: string; image?: string }>()
</script>

<template>
  <div class="slidev-layout layout-section" :class="{ 'with-art': image }">
    <div class="wrap">
      <div v-if="kicker" class="kicker">{{ kicker }}</div>
      <slot />
    </div>
    <div v-if="image" class="section-art deck-art-circle" :style="{ backgroundImage: `url(${image})` }" />
  </div>
</template>

<style scoped>
.layout-section {
  background: var(--navy);
  height: 100%;
  display: flex;
  align-items: center;
  padding: 2.2rem 4rem;
}
/* optional spot art on the right; see ART.md */
.layout-section.with-art { display: grid; grid-template-columns: 1.45fr 1fr; gap: 2.4rem; align-items: center; }
.kicker {
  font-size: 0.9rem;
  font-weight: 800;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 0.9rem;
}
.wrap { max-width: 52rem; }
.wrap :deep(h1) {
  color: var(--cream);
  font-size: 3rem;   /* act titles are full claims now, not one-word topics */
  line-height: 1.12;
  text-wrap: balance;
  margin: 0;
}

/* --muted is tuned for the cream ground and lands at 1.7:1 on navy - invisible.
   Captions on a dark divider need a light tone. */
.layout-section :deep(.caption) {
  color: #C7D0D4;
  max-width: 52rem;
}
.layout-section :deep(.caption.gold) {
  color: var(--cream);
  border-left-color: var(--gold);
}
.layout-section :deep(.caption strong) { color: var(--cream); }
</style>
