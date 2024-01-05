<script setup>
import { defineProps } from 'vue'
import HMACSHA256 from './HMACSHA256.vue'
import HexadecimalstoDecimal from './HexadecimalstoDecimal.vue'
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div class="result">
    <div class="row-wrap svelte-1j9612g">
      <h2
        class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
        style="">Final Result</h2>
      <div class="scrollX crash-result">
        <div class="wrap svelte-1lfzokq"><span
            class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
            style="font-family: monospace;">{{data.finalResult}}</span>
        </div>
      </div>
    </div>
    <div class="row-wrap svelte-1j9612g">
      <h2
        class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
        style="">Casino Seeds to Hexadecimals</h2>
      <HMACSHA256 :secret="data.serverSeed" 
        :message="data.clientSeed" 
        :highLightCount="4" ></HMACSHA256>
  </div>
  <div class="row-wrap svelte-1j9612g">
    <h2
      class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
      style="">Hexadecimals to Decimal</h2>
    <div class="wrap scrollX" style="display: flex;flex-direction: row;">
        <template v-for="idx in [0]">
            <HexadecimalstoDecimal :secret="data.serverSeed" 
            :message="data.clientSeed"
            :byteIndex="idx" :maxRange="2"></HexadecimalstoDecimal>
        </template>
    </div>
  </div>
  <div class="row-wrap svelte-1j9612g">
    <h2
      class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
      style="">Raw to Edged</h2>
      <div class="scrollX">
        <div class="wrap svelte-1lfzokq">
          4294967296 / (
          <span 
            class="highlight weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
            style="font-family: monospace;">{{data.result}}</span>
          + 1) * (1 - 0.03) = 
          <span 
          class="highlight weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
          style="font-family: monospace;">{{data.finalResult}}</span>
        </div>
      </div>
  </div>
</div></template>

<style scoped>

.row-wrap {
  display: flex;
  flex-direction: column;
  max-width: 700px;
}

h2 {
  padding: 0.5em 0;
}

.highlight {
  color: white !important;
  font-weight: 500;
}

.column {
  display: flex;
  width: -webkit-fit-content;
  width: -moz-fit-content;
  width: fit-content;
  flex-direction: column;
}

.scrollX div:not(:first-child) {
  margin-left: 4rem;
}

.result .crash-result span {
    color:white;
}

</style>
