<script setup>
import Dice from "./dice.vue";
</script>

<template>
  <div class="wrap svelte-wtusq6">
    <Dice />
  </div>
</template>

<style scoped>
.wrap.svelte-wtusq6 {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: left;
  min-height: 200px;
  padding: var(--spacingEm-1);
  border: dotted 2px var(--grey-400);
  border-radius: var(--border-radius-0-5);
}

.wrap.svelte-wtusq6 > * + * {
  margin-top: var(--spacingEm-1);
}
</style>
