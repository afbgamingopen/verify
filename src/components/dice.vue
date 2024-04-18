<script setup>
import { defineProps } from "vue";
import Slider from "./dice-slider.vue";
import Slide from "./dice-slide.vue";
import Result from "./dice-result.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div>
    <div class="wrap svelte-q19e8x">
      <div class="dice-wrap svelte-q19e8x">
        <Slider :data="data" />
      </div>
      <Slide :data="data" />
    </div>
    <Result :data="data" />
  </div>
</template>

<style scoped>
.wrap.svelte-q19e8x {
  position: relative;
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 700px;
  border: dotted 2px var(--grey-400);
  padding: 1em;
}

.dice-wrap.svelte-q19e8x {
  position: absolute;
  width: calc(100% - 3em);
  height: 100%;
}
</style>
