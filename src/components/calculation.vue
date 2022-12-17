<script setup>
import { reactive } from 'vue'
import { parseQuery } from "vue-router"
import sha256 from 'crypto-js/sha256';
import hmacSHA256 from 'crypto-js/hmac-sha256';
import Hex from 'crypto-js/enc-hex';

import Dice from './dice.vue'
import SingleBaccarat from './singleBaccarat.vue'

let query = parseQuery(location.search);

const data = reactive({
    game: query['game']?query['game']:'',
    clientSeed: query['clientSeed']?query['clientSeed']:'',
    serverSeed: query['serverSeed']?query['serverSeed']:'',
    nonce: query['nonce']?query['nonce']:1,
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
        calcDice();
    }else if(data.game == "singleBaccarat") {
        calcSingleBaccarat();
    }
}

function calcDice() {
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

function calcSingleBaccarat() {
  const hmacDigest = hmacSHA256(data.clientSeed + ":" + data.nonce + ":0", data.serverSeed);
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  const hmacDigestHex = Hex.stringify(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  data.hmacDigestHex = hmacDigestHex;
  data.resultPow = [0, 0, 0, 0, 0, 0];
  data.result = [0, 0, 0, 0, 0, 0];
  data.resultXS = [0, 0, 0, 0, 0, 0];
  data.finalResult = [0, 0, 0, 0, 0, 0];
  data.finalPoker = [0, 0, 0, 0, 0, 0];
  for (let idx = 0; idx < 6; idx++) {
    data.resultPow[idx] = hmacDigestBytes[idx * 4 + 0] / Math.pow(256, 1) +
      hmacDigestBytes[idx * 4 + 1] / Math.pow(256, 2) +
      hmacDigestBytes[idx * 4 + 2] / Math.pow(256, 3) +
      hmacDigestBytes[idx * 4 + 3] / Math.pow(256, 4);
    data.result[idx] = data.resultPow[idx] * 52;
    data.resultXS[idx] = data.result[idx].toFixed(20)
    data.resultXS[idx] = data.resultXS[idx].substr(data.resultXS[idx].indexOf("."), 13)
    data.finalResult[idx] = (Math.floor(data.result[idx]));
    data.finalPoker[idx] = window.pokers[data.finalResult[idx]];
  }

  data.playerPoker = [data.finalPoker[0], data.finalPoker[2]];
  data.bankerPoker = [data.finalPoker[1], data.finalPoker[3]];
  data.playerPoint = data.finalPoker[0].baccaretPoint + data.finalPoker[2].baccaretPoint
  data.bankerPoint = data.finalPoker[1].baccaretPoint + data.finalPoker[3].baccaretPoint
  data.playerPoint = data.playerPoint % 10;
  data.bankerPoint = data.bankerPoint % 10;

  if (data.playerPoint < 8 && data.bankerPoint < 8) {
    let nextPoker = data.finalPoker[4];
    switch(data.playerPoint) {
      case 0:
      case 1:
      case 2:
      case 3:
      case 4:
      case 5:
        data.playerPoker.push(nextPoker);
        data.playerPoint += nextPoker.baccaretPoint;
        nextPoker = data.finalPoker[5];
        data.playerPoint = data.playerPoint % 10;
        let playerDrawPokerPoint = nextPoker.baccaretPoint;
        switch (data.bankerPoint) {
          case 0:
          case 1:
          case 2:
            data.bankerPoint += nextPoker.baccaretPoint
            data.bankerPoker.push(nextPoker);
            data.bankerPoint = data.bankerPoint % 10;
            break;
          case 3:
            if (playerDrawPokerPoint != 8) {
              data.bankerPoint += nextPoker.baccaretPoint
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 4:
            if ([0, 1, 8, 9].indexOf(playerDrawPokerPoint) == -1) {
              data.bankerPoint += nextPoker.baccaretPoint
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 5:
            if ([0, 1, 2, 3, 8, 9].indexOf(playerDrawPokerPoint) == -1) {
              data.bankerPoint += nextPoker.baccaretPoint
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 6:
            if ([6, 7].indexOf(playerDrawPokerPoint) >= 0) {
              data.bankerPoint += nextPoker.baccaretPoint
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
        }
        break;
      case 6:
      case 7:
        if([0,1,2,3,4,5].indexOf(data.bankerPoint) >= 0) {
          data.bankerPoint += nextPoker.baccaretPoint
          data.bankerPoker.push(nextPoker);
          data.bankerPoint = data.bankerPoint % 10;
        }
        break;
    }
  }
  
  if (data.playerPoint > data.bankerPoint) {
    data.playerWin = "win";
    data.bankerWin = "lose";
  } else if (data.playerPoint == data.bankerPoint) {
    data.playerWin = "none";
    data.bankerWin = "none";
  } else {
    data.playerWin = "lose";
    data.bankerWin = "win";
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

calc();

</script>

<template>
  <div class="content">
    <div class="calccontent">
        <el-form ref="form" :model="data" label-width="80px" label-position="top">
            <el-form-item label="Game">
              <el-select v-model="data.game" placeholder="Please Selece Game" @change="handleChange">
                <el-option label="Dice" value="dice"></el-option>
                <el-option label="Single Baccarat" value="singleBaccarat"></el-option>
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
    <SingleBaccarat v-if="data.game==='singleBaccarat'" :data="data" ></SingleBaccarat>
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

.calccontent input {
  color: white !important;;
}

</style>
