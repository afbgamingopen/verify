<script setup>
import { defineProps } from 'vue'
import Slider from './dice-slider.vue'
import Slide from './dice-slide.vue'
import Result from './dice-result.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
const index03 = [0,1,2,3]
const index4 = [4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
</script>

<template>
  <div class="result">
    <div class="row-wrap">
      <h2>Final Result</h2>
      <div class="scrollX"><span class="highlight" style="font-family: monospace;">{{data.finalResult}}</span></div>
    </div>
    <div class="row-wrap">
      <h2
        style="">Casino Seeds to Bytes</h2>
      <div class="scrollX"><span class="highlight" style="font-family: monospace;">HMAC_SHA256({{data.serverSeed}},{{data.clientSeed}}:{{data.nonce}}:0)</span>
        <table>
          <tbody>
            <tr class="tr">
              <td class="td" v-for="n in index03">
                <span class="highlight" style="font-family: monospace;">{{data.hmacDigestHex.substring(n*2,n*2+2)}}</span>
              </td>
              <td class="td" v-for="n in index4">
                <span style="font-family: monospace;">{{data.hmacDigestHex.substring(n*2,n*2+2)}}</span>
              </td>
            </tr>
            <tr class="tr">
              <td class="td" v-for="n in index03">
                <span class="highlight" style="font-family: monospace;">{{data.hmacDigestBytes[n]}}</span>
              </td>
              <td class="td" v-for="n in index4">
                <span style="font-family: monospace;">{{data.hmacDigestBytes[n]}}</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="row-wrap">
      <h2 style="">Bytes to Number</h2>
      <div class="wrap scrollX">
        <div class="column">
          <span class="highlight" style="font-family: monospace; white-space: nowrap;">
            ({{data.hmacDigestBytes[0]}}, {{data.hmacDigestBytes[1]}}, {{data.hmacDigestBytes[2]}}, {{data.hmacDigestBytes[3]}}) -&gt; [0, ..., 10000] = {{(data.finalResult*100).toFixed(0)}})</span>
          <table>
            <tbody>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);">
                  <span style="font-family: monospace; white-space: nowrap;"> </span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight" 
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[0]/Math.pow(256,1)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td">
                  <span style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[0]}} / (256 ^ 1))</span>
                </td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[1]/Math.pow(256,2)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[1]}} / (256 ^ 2))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[2]/Math.pow(256,3)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[2]}} / (256 ^ 3))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">+</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.hmacDigestBytes[3]/Math.pow(256,4)).toFixed(12).substring(1,14)}}</span></td>
                <td class="td"><span
                    style="font-family: monospace; white-space: nowrap;">
                    ({{data.hmacDigestBytes[3]}} / (256 ^ 4))</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">=</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">0</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{(data.resultPow).toFixed(12).substring(1,14)}}</span></td>
                <td class="td" style="text-align: right;"><span
                    style="font-family: monospace; white-space: nowrap;">(* 10001)</span></td>
              </tr>
              <tr>
                <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">=</span></td>
                <td class="td" style="text-align: right;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{Math.floor(data.result)}}</span></td>
                <td class="td" style="text-align: left;padding:0;"><span class="highlight"
                    style="font-family: monospace; white-space: nowrap;">
                    {{data.resultXS}}</span></td>
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
  padding-top: 0.5em;
}

.highlight {
  color: white;
  font-weight: 500;
}

</style>
