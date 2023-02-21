<script setup>
import { defineProps } from 'vue'
import HMACSHA256 from './HMACSHA256.vue'
import BytesToNumber from './BytesToNumber.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
</script>

<template>
  <div class="result">
    <div class="row-wrap">
      <h2>Final Result</h2>
      <div class="scrollX">
        <span class="highlight" style="font-family: monospace;">
          <table>
            <tbody>
              <tr class="tr svelte-1b0xvv1">
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[0]}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[1]}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[2]}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[3]}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[4]}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalResult[5]}}</span> </td>
              </tr>
              <tr class="tr svelte-1b0xvv1">
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[0].name}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[1].name}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[2].name}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[3].name}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[4].name}}</span> </td>
                <td class="td svelte-1b0xvv1"><span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-129khay"
                    style="font-family: monospace;">{{data.finalPoker[5].name}}</span> </td>
              </tr>
            </tbody>
          </table>
        </span>
      </div>
    </div>
    <div class="row-wrap">
      <h2 style="">Casino Seeds to Bytes</h2>
      <HMACSHA256 :secret="data.serverSeed" 
        :message="data.clientSeed+':'+data.nonce+':'+data.cursor" 
        :highLightCount="24" ></HMACSHA256>
    </div>
    <div class="row-wrap">
      <h2 style="">Bytes to Number</h2>
      <div class="wrap scrollX" style="display: flex;flex-direction: row;">
        <template v-for="idx in [0,4,8,12,16,20]">
          <BytesToNumber :secret="data.serverSeed" 
          :message="data.clientSeed+':'+data.nonce+':'+data.cursor"
          :byteIndex="idx" :maxRange="52"></BytesToNumber>
        </template>
      </div>
    </div>
  </div>
</template>

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

.scrollX div:not(:first-child){
  margin-left: 4rem;
}

</style>
