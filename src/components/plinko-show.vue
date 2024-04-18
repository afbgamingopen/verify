<script setup>
import { defineProps } from "vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div class="wrap svelte-wtusq6">
    <div class="wrap svelte-5dszz2">
      <div class="content svelte-5dszz2">
        <div
          class="payout svelte-nb62ae"
          style="background: rgb(255, 137, 18); --shadow-color: #a94400"
        >
          <span class="content">{{ data.finalResult }}×</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrap.svelte-wtusq6 {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: left;
  height: 200px;
  max-width: 700px;
  padding: var(--spacingEm-1);
  border: dotted 2px var(--grey-400);
  border-radius: var(--border-radius-0-5);
}

.wrap.svelte-wtusq6 > * + * {
  margin-top: var(--spacingEm-1);
}

.wrap.svelte-5dszz2 {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: var(--spacing-2-5);
}

.content.svelte-5dszz2 {
  display: grid;
  grid-gap: 1%;
  height: 100%;
  width: var(--spacing-3);
}

.content.svelte-5dszz2 > * {
  grid-row: 1;
}

@-webkit-keyframes svelte-nb62ae-slideDown {
  0%,
  to {
    transform: translate(0);
  }

  50% {
    transform: translateY(30%);
  }
}

@keyframes svelte-nb62ae-slideDown {
  0%,
  to {
    transform: translate(0);
  }

  50% {
    transform: translateY(30%);
  }
}

.payout.svelte-nb62ae {
  position: relative;
  cursor: help;
  border-radius: 0.3em;
  text-align: center;
  -webkit-animation-duration: 0.3s !important;
  animation-duration: 0.3s !important;
  -webkit-animation-timing-function: cubic-bezier(0.18, 0.89, 0.32, 1.28);
  animation-timing-function: cubic-bezier(0.18, 0.89, 0.32, 1.28);
  box-shadow: 0 0.2em 0 0 var(--shadow-color);
}

.payout.highlighted.svelte-nb62ae {
  -webkit-animation-name: svelte-nb62ae-slideDown;
  animation-name: svelte-nb62ae-slideDown;
}

.payout.svelte-nb62ae > span {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  color: #000c;
  font-size: 0.75em;
}

.payout.svelte-nb62ae > span {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  color: #000c;
  font-size: 0.75em;
}

.content {
  min-height: var(--spacing-2-5);
}
</style>
