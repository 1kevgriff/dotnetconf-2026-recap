<!-- Headline-only. One claim, nothing else on screen. -->
<script setup lang="ts">
defineProps<{ image?: string }>()
</script>

<template>
  <div class="slidev-layout layout-statement" :class="{ 'with-art': image }">
    <div class="wrap"><slot /></div>
    <div v-if="image" class="statement-art deck-art-circle" :style="{ backgroundImage: `url(${image})` }" />
  </div>
</template>

<style scoped>
.layout-statement {
  height: 100%;
  display: flex;
  align-items: center;
  padding: 2.2rem 4rem;
}
.wrap { max-width: 52rem; }
/* optional spot art on the right; see ART.md */
.layout-statement.with-art { display: grid; grid-template-columns: 1.45fr 1fr; gap: 2.4rem; align-items: center; }
.wrap :deep(p),
.wrap :deep(blockquote p) {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1.15;
  text-wrap: balance;
  letter-spacing: -0.02em;
  color: var(--navy);
  margin: 0 0 0.6rem;
}
.wrap :deep(blockquote) { border-left: 4px solid var(--gold); padding-left: 1.6rem; }

/* A caption here is SUPPORTING text, not the claim. Without this it inherits the 2.1rem
   statement type and the slide reads as three equally important sentences. */
.wrap :deep(.caption),
.wrap :deep(.caption p) {
  font-size: 1.05rem;
  font-weight: 400;
  line-height: 1.5;
  letter-spacing: 0;
  color: var(--muted);
  margin: 1.1rem 0 0;
}
</style>
