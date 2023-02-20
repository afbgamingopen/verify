<script setup>
import { defineProps } from 'vue'
import Show from './singleBaccarat-show.vue'
import Result from './singleBaccarat-result.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
console.log(data.game)
</script>

<template>
  <div>
    <Show :data="data"/>
    <Result :data="data"/>
  </div>
</template>

<style scoped>

.wrap.svelte-q19e8x {
  position: relative;
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 700px
}

.dice-wrap.svelte-q19e8x {
  position: absolute;
  width: calc(100% - 3em);
  height: 100%
}

</style>
