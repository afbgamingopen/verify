<script setup>
import { defineProps, ref, watch } from "vue";
import Slider from "./dice-slider.vue";
import Slide from "./dice-slide.vue";
import Result from "./dice-result.vue";
import StakeLoad from "./stakeLoad.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
const isOpen = ref(false);
watch(props, () => {
  if (
    props.data.clientSeed === "" ||
    props.data.serverSeed === "" ||
    props.data.game === "" ||
    props.data.nonce === 0
  ) {
    isOpen.value = true;
  } else {
    isOpen.value = false;
  }
});
</script>

<template>
  <div>
    <div class="wrap svelte-q19e8x">
      <StakeLoad v-if="isOpen" />
      <div class="dice-wrap svelte-q19e8x" v-if="!isOpen">
        <Slider :data="data" />
      </div>
      <Slide :data="data" v-if="!isOpen" />
    </div>
    <Result :data="data" v-if="!isOpen" />
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
