<!-- One headline, one stream screenshot filling the rest of the slide. -->
<script setup lang="ts">
defineProps<{ image: string; time?: string }>()
</script>

<template>
  <div class="slidev-layout layout-shot">
    <slot />
    <div class="shot-frame">
      <img :src="image" class="shot-img" alt="Screenshot from the .NET Conf 2026 stream" />
      <span v-if="time" class="shot-time">{{ time }} ET</span>
    </div>
  </div>
</template>

<style scoped>
.layout-shot {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: 2rem 3rem 1.6rem;
}
.layout-shot :deep(h1) { flex: none; font-size: 2rem; margin-bottom: 0.9rem; }
.layout-shot :deep(h1 + p) { opacity: 1; margin: -0.4rem 0 0.8rem; font-size: 1.1rem; color: var(--muted); }
.shot-frame { flex: 1; min-height: 0; position: relative; display: flex; justify-content: center; }
.shot-img { max-height: 100%; max-width: 100%; object-fit: contain; border-radius: 10px; box-shadow: 0 6px 24px rgba(0, 0, 0, 0.18); }
.shot-time {
  position: absolute; right: 0; bottom: -1.3rem;
  font-size: 0.7rem; letter-spacing: 0.12em; color: var(--muted);
}
</style>
