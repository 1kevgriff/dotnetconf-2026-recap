<!-- Session divider: one per conference session. Gold ground so it reads apart from in-session section slides. -->
<script setup lang="ts">
defineProps<{ num?: string | number; time?: string; speakers?: string }>()
</script>

<template>
  <div class="slidev-layout layout-session">
    <div v-if="num" class="num">{{ String(num).padStart(2, '0') }}</div>
    <div class="body">
      <div v-if="time" class="time">{{ time }} ET</div>
      <slot />
      <div v-if="speakers" class="speakers">{{ speakers }}</div>
    </div>
  </div>
</template>

<style scoped>
.layout-session {
  background: var(--gold);
  height: 100%;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 3rem;
  align-items: center;
  padding: 2.4rem 4rem;
}
.num {
  font-size: 9rem;
  font-weight: 800;
  line-height: 1;
  color: var(--navy);
  opacity: 0.9;
}
.time {
  font-size: 0.9rem;
  font-weight: 800;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--navy);
  margin-bottom: 0.9rem;
}
.body :deep(h1) {
  color: var(--navy);
  font-size: 2.8rem;
  line-height: 1.12;
  text-wrap: balance;
  margin: 0;
}
.speakers {
  margin-top: 1.2rem;
  font-size: 1.3rem;
  color: var(--navy);
}
</style>
