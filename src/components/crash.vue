<script setup>
import { defineProps, ref, watch, onMounted } from "vue";
import Show from "./crash-show.vue";
import Result from "./crash-result.vue";
import StakeLoad from "./stakeLoad.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
const isOpen = ref(false);
onMounted(() => {
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
    <div class="wrap svelte-q19e8x" v-if="isOpen">
      <StakeLoad />
    </div>
    <Show :data="data" v-if="!isOpen" />
    <Result :data="data" v-if="!isOpen" />
  </div>
</template>

<style scoped>
.wrap.svelte-q19e8x {
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 700px;
  border: dotted 2px var(--grey-400);
  padding: 3.5em 1em 1em;
}
</style>
