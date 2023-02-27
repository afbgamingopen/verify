<script setup>
import { defineProps } from 'vue'
import Show from './crash-show.vue'
import Result from './crash-result.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
</script>

<template>
  <div>
    <Show :data="data"/>
    <Result :data="data"/>
  </div>
</template>

<style scoped>

</style>
