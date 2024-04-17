<script setup>
import {reactive, defineProps, watch } from 'vue'
import hmacSHA256 from 'crypto-js/hmac-sha256';
import Hex from 'crypto-js/enc-hex';

const props = defineProps({
	secret: String,
  message: String,
  byteIndex: Number,
  maxRange: Number
});
console.log("props",props);
watch(props, () => {
  calc();
})
const calced = reactive({digest:[],digestBytes:[],resultPow:0,result:0,resultXS:0.0,finalResult:0})
calc();

function calc() {
  calced.digest = hmacSHA256(props.message, props.secret);
  let bytes = hmacDigestToBytes(calced.digest);
  calced.digestBytes = bytes;
  calced.resultPow = bytes[0+props.byteIndex]/Math.pow(256,1) + 
          bytes[1+props.byteIndex]/Math.pow(256,2) +
          bytes[2+props.byteIndex]/Math.pow(256,3) +
          bytes[3+props.byteIndex]/Math.pow(256,4);
  calced.result = calced.resultPow * props.maxRange;
  calced.resultXS = calced.result.toFixed(20)
  calced.resultXS = calced.resultXS.substr(calced.resultXS.indexOf("."), 13)
  calced.finalResult = (Math.floor(calced.result)/100);
  console.log(1111,calced.result);
  console.log(2222,calced.finalResult);
}

function hmacDigestToBytes(wordArray) {
    // Shortcuts
    var words = wordArray.words;
    var sigBytes = wordArray.sigBytes;
    // Convert
    var bytes = [];
    for (var i = 0; i < sigBytes; i++) {
        var bite = (words[i >>> 2] >>> (24 - (i % 4) * 8)) & 0xff;
        bytes.push(bite &0xff);
    }
    return bytes;
}
</script>

<template>
  <div class="column">
    <span class="highlight" style="font-family: monospace; white-space: nowrap;">
      ({{calced.digestBytes[props.byteIndex+0]}}, {{calced.digestBytes[props.byteIndex+1]}}, {{calced.digestBytes[props.byteIndex+2]}}, {{calced.digestBytes[props.byteIndex+3]}}) -&gt; [0, ..., {{ props.maxRange-1 }}] = {{(calced.finalResult*100).toFixed(0)}}</span>
    <table>
      <tbody>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);">
            <span style="font-family: monospace; white-space: nowrap;"> </span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">0</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">
              {{(calced.digestBytes[props.byteIndex+0]/Math.pow(256,1)).toFixed(12).substring(1,14)}}</span></td>
          <td class="td">
            <span style="font-family: monospace; white-space: nowrap;">
              ({{calced.digestBytes[props.byteIndex+0].toString().padStart(3,'0')}} / (256 ^ 1))</span>
          </td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">0</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{(calced.digestBytes[props.byteIndex+1]/Math.pow(256,2)).toFixed(12).substring(1,14)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{calced.digestBytes[props.byteIndex+1].toString().padStart(3,'0')}} / (256 ^ 2))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">0</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{(calced.digestBytes[props.byteIndex+2]/Math.pow(256,3)).toFixed(12).substring(1,14)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{calced.digestBytes[props.byteIndex+2].toString().padStart(3,'0')}} / (256 ^ 3))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">0</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{(calced.digestBytes[props.byteIndex+3]/Math.pow(256,4)).toFixed(12).substring(1,14)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{calced.digestBytes[props.byteIndex+3].toString().padStart(3,'0')}} / (256 ^ 4))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">=</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">0</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{(calced.resultPow).toFixed(12).substring(1,14)}}</span></td>
          <td class="td" style="text-align: right;"><span
              style="font-family: monospace; white-space: nowrap;">(* {{ props.maxRange }})</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">=</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{Math.floor(calced.result)}}</span></td>
          <td class="td" style="text-align: left;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{calced.resultXS}}</span></td>
        </tr>
      </tbody>
    </table>
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
  color: white;
  font-weight: 500;
}

</style>
