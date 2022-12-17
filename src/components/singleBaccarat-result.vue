<script setup>
import { defineProps } from 'vue'
import Slider from './dice-slider.vue'
import Slide from './dice-slide.vue'
import Result from './dice-result.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
const indexHighLight = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23]
const indexRemain = [24,25,26,27,28,29,30,31]
const indexResultPow = [0,1,2,3,4,5]
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
      <h2
        style="">Casino Seeds to Bytes</h2>
      <div class="scrollX"><span class="highlight" style="font-family: monospace;">HMAC_SHA256({{data.serverSeed}},{{data.clientSeed}}:{{data.nonce}}:{{data.cursor}})</span>
        <table>
          <tbody>
            <tr class="tr">
              <td class="td" v-for="n in indexHighLight">
                <span class="highlight" style="font-family: monospace;">{{data.hmacDigestHex.substring(n*2,n*2+2)}}</span>
              </td>
              <td class="td" v-for="n in indexRemain">
                <span style="font-family: monospace;">{{data.hmacDigestHex.substring(n*2,n*2+2)}}</span>
              </td>
            </tr>
            <tr class="tr">
              <td class="td" v-for="n in indexHighLight">
                <span class="highlight" style="font-family: monospace;">{{data.hmacDigestBytes[n]}}</span>
              </td>
              <td class="td" v-for="n in indexRemain">
                <span style="font-family: monospace;">{{data.hmacDigestBytes[n]}}</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="row-wrap">
      <h2 style="">Bytes to Number</h2>
      <div class="wrap scrollX" style="display: flex;flex-direction: row;">
        <div class="column" v-for="idx in indexResultPow">
          <span class="highlight" style="font-family: monospace; white-space: nowrap;">
            ({{data.hmacDigestBytes[idx*4+0]}}, {{data.hmacDigestBytes[idx*4+1]}}, {{data.hmacDigestBytes[idx*4+2]}}, {{data.hmacDigestBytes[idx*4+3]}}) -&gt; [0, ..., 51] = {{(data.finalResult[idx]).toFixed(0)}})</span>
          <table>
            <tbody>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);">
                  <span style="font-family: monospace; white-space: nowrap;"> </span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight" 
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[idx*4+0]/Math.pow(256,1)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;">
                  <span style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[idx*4+0].toString().padStart(3,'0')}} / (256 ^ 1))</span>
                </td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[idx*4+1]/Math.pow(256,2)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[idx*4+1].toString().padStart(3,'0')}} / (256 ^ 2))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[idx*4+2]/Math.pow(256,3)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[idx*4+2].toString().padStart(3,'0')}} / (256 ^ 3))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[idx*4+3]/Math.pow(256,4)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[idx*4+3].toString().padStart(3,'0')}} / (256 ^ 4))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">=</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.resultPow[idx]).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;"><span
                    style="font-family: monospace; white-space: nowrap;">(* 52)</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">=</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{Math.floor(data.result[idx])}}</span></td>
                <td class="td" style="text-align: left;padding:0;"><span
                    style="font-family: monospace; white-space: nowrap;">
                    {{data.resultXS[idx]}}</span></td>
              </tr>
            </tbody>
          </table>
        </div>
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
