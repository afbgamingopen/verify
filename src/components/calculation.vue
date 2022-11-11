<script setup>
import { reactive } from 'vue'
import sha256 from 'crypto-js/sha256';
import hmacSHA256 from 'crypto-js/hmac-sha256';
import Hex from 'crypto-js/enc-hex';

import Dice from './dice.vue'

const data = reactive({
  game: '',
  clientSeed: '',
  serverSeed: '',
  nonce: 1,
  cursor: 0,
  resultPow: 0,
  result: 0,
  resultXS: '',
  finalResult: '',
  hmacDigest: '',
  hmacDigestBytes: [],
  hmacDigestHex: '',
})

function handleChange() {
  calc();
}

function calc() {
  if(data.game == "dice") {
    const hmacDigest = hmacSHA256(data.clientSeed+":"+data.nonce+":0", data.serverSeed);
    const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
    const hmacDigestHex = Hex.stringify(hmacDigest);
    data.hmacDigest = hmacDigest;
    data.hmacDigestBytes = hmacDigestBytes;
    data.hmacDigestHex = hmacDigestHex;
    data.resultPow = hmacDigestBytes[0]/Math.pow(256,1) + 
      hmacDigestBytes[1]/Math.pow(256,2) +
      hmacDigestBytes[2]/Math.pow(256,3) +
      hmacDigestBytes[3]/Math.pow(256,4);
    data.result = data.resultPow * 10001;
    data.resultXS = data.result.toFixed(20)
    data.resultXS = data.resultXS.substr(data.resultXS.indexOf("."), 13)
    data.finalResult = (Math.floor(data.result)/100);
  }
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
  <div class="content">
    <div class="calccontent">
        <el-form ref="form" :model="data" label-width="80px" label-position="top">
            <el-form-item label="Game">
              <el-select v-model="data.game" placeholder="Please Selece Game" @change="handleChange">
                <el-option label="Dice" value="dice"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Client Seed">
                <el-input v-model="data.clientSeed" @input="handleChange"></el-input>
            </el-form-item>
            <el-form-item label="Server Seed">
                <el-input v-model="data.serverSeed" @input="handleChange"></el-input>
            </el-form-item>
            <el-form-item label="Nonce">
                <el-input-number v-model="data.nonce" @change="handleChange" :min="1" label="Nonce"></el-input-number>
            </el-form-item>
          </el-form>
    </div>
    <div>
      <code id="coderesult">
      </code>
    </div>
  <div>
    <Dice v-if="data.game==='dice'" :data="data" ></Dice>
  </div>
  </div>
</template>

<style scoped>
.calccontent {
  max-width: 700px;
}
.el-select {
  width: 100%;
}

.el-input-number {
  width: 100%;
}

</style>
