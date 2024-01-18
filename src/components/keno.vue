<script setup>
import { defineProps } from 'vue'
import Show from './keno-show.vue'
import Result from './keno-result.vue'
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
