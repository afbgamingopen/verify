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
watch(props, () => {
  calc();
})
const calced = reactive({digest:[],digestBytes:[],resultPow:0,result:0,resultXS:0.0,finalResult:0})
calc();

function calc() {
  calced.digest = hmacSHA256(props.message, props.secret);
  let bytes = hmacDigestToBytes(calced.digest);
  calced.digestBytes = bytes;
  calced.resultPow = (bytes[0] >> 4) * Math.pow(16,7) +
                   (bytes[0] & 0xf) * Math.pow(16,6) +
                   (bytes[1] >> 4) * Math.pow(16,5) +
                   (bytes[1] & 0xf) * Math.pow(16,4) +
                   (bytes[2] >> 4) * Math.pow(16,3) +
                   (bytes[2] & 0xf) * Math.pow(16,2) +
                   (bytes[3] >> 4) * Math.pow(16,1) +
                   (bytes[3] & 0xf) * Math.pow(16,0);;
  calced.result = calced.resultPow * props.maxRange;
  calced.resultXS = calced.result.toFixed(20)
  calced.resultXS = calced.resultXS.substr(calced.resultXS.indexOf("."), 13)
  calced.finalResult = (Math.floor(calced.result)/100);
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

function hexChar(i) {
  return "0123456789abcdef"[i];
}
</script>

<template>
  <div class="column">
    <span class="highlight" style="font-family: monospace; white-space: nowrap;">
      ({{hexChar(calced.digestBytes[props.byteIndex+0]>>4)}}, {{hexChar(calced.digestBytes[props.byteIndex+0] & 0xf)}}, 
       {{hexChar(calced.digestBytes[props.byteIndex+1]>>4)}}, {{hexChar(calced.digestBytes[props.byteIndex+1] & 0xf)}}, 
       {{hexChar(calced.digestBytes[props.byteIndex+2]>>4)}}, {{hexChar(calced.digestBytes[props.byteIndex+2] & 0xf)}}, 
       {{hexChar(calced.digestBytes[props.byteIndex+3]>>4)}}, {{hexChar(calced.digestBytes[props.byteIndex+3] & 0xf)}}) = {{calced.resultPow.toFixed(0)}}</span>
    <table>
      <tbody>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);">
            <span style="font-family: monospace; white-space: nowrap;"> </span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+0]>>4)*Math.pow(16,7)).toFixed(0)}}</span></td>
          <td class="td">
            <span style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+0]>>4)}} * (16 ^ 7))</span>
          </td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+0] & 0xf)*Math.pow(16,6)).toFixed(0)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+0] & 0xf)}} * (16 ^ 6))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);">
            <span style="font-family: monospace; white-space: nowrap;" class="highlight">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+1]>>4)*Math.pow(16,5)).toFixed(0)}}</span></td>
          <td class="td">
            <span style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+1]>>4)}} * (16 ^ 5))</span>
          </td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+1] & 0xf)*Math.pow(16,4)).toFixed(0)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+1] & 0xf)}} * (16 ^ 4))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);">
            <span style="font-family: monospace; white-space: nowrap;" class="highlight">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+2]>>4)*Math.pow(16,3)).toFixed(0)}}</span></td>
          <td class="td">
            <span style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+2]>>4)}} * (16 ^ 3))</span>
          </td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+2] & 0xf)*Math.pow(16,2)).toFixed(0)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+2] & 0xf)}} * (16 ^ 2))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);">
            <span style="font-family: monospace; white-space: nowrap;" class="highlight">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight" 
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+3]>>4)*Math.pow(16,1)).toFixed(0)}}</span></td>
          <td class="td">
            <span style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+3]>>4)}} * (16 ^ 1))</span>
          </td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">+</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{((calced.digestBytes[props.byteIndex+3] & 0xf)*Math.pow(16,0)).toFixed(0)}}</span></td>
          <td class="td"><span
              style="font-family: monospace; white-space: nowrap;">
              ({{hexChar(calced.digestBytes[props.byteIndex+3] & 0xf)}} * (16 ^ 0))</span></td>
        </tr>
        <tr>
          <td class="td" style="padding-right: var(--spacing-1);"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">=</span></td>
          <td class="td" style="text-align: right;padding:0;"><span class="highlight"
              style="font-family: monospace; white-space: nowrap;">
              {{calced.resultPow.toFixed(0)}}</span></td>
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
