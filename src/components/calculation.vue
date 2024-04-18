<script setup>
import { reactive } from "vue";
import { parseQuery } from "vue-router";
import hmacSHA256 from "crypto-js/hmac-sha256";

import Crash from "./crash.vue";
import Dice from "./dice.vue";
import Plinko from "./plinko.vue";
import SingleBaccarat from "./singleBaccarat.vue";
import Keno from "./keno.vue";
import Roulette from "./Roulette.vue";

let query = parseQuery(location.search);

const data = reactive({
  game: query["game"] ? query["game"] : "",
  clientSeed: query["clientSeed"] ? query["clientSeed"] : "",
  serverSeed: query["serverSeed"] ? query["serverSeed"] : "",
  serverSeedHash: query["serverSeedHash"] ? query["serverSeedHash"] : "",
  nonce: query["nonce"] ? query["nonce"] : 1,
  cursor: 0,
  risk: query["risk"] ? query["risk"].toLowerCase() : "normal",
  rows: query["rows"] ? query["rows"] : "16",

  result: 0,
  calcResult: "",
  finalResult: "",
  hmacDigest: "",
  hmacDigestBytes: [],

  plinkoPayout: [],
  plinkoRows: [],
  plinkoPayoutIndex: "",

  kenoNumberToShuffle: [],
  kenoCalcResult: [],
  kenoFinalResult: [],
});

function handleChange() {
  calc();
}
function calc() {
  if (data.game == "dice") {
    calcDice();
  } else if (data.game == "singleBaccarat") {
    calcSingleBaccarat();
  } else if (data.game == "plinko") {
    calcPlinko();
  } else if (data.game == "crash") {
    calcCrash();
  } else if (data.game == "keno") {
    calcKeno();
  } else if (data.game == "roulette") {
    calcRoulette();
  }
}

function calcDice() {
  const hmacDigest = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":0",
    data.serverSeed
  );
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  data.finalResult =
    Math.floor(bytesToNumber(data.hmacDigestBytes, 0, 10001)) / 100;
}

function calcSingleBaccarat() {
  const hmacDigest = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":0",
    data.serverSeed
  );
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  data.result = [0, 0, 0, 0, 0, 0];
  data.finalResult = [0, 0, 0, 0, 0, 0];
  data.finalPoker = [0, 0, 0, 0, 0, 0];
  for (let idx = 0; idx < 6; idx++) {
    data.result[idx] = bytesToNumber(data.hmacDigestBytes, idx * 4, 52);
    data.finalResult[idx] = Math.floor(data.result[idx]);
    data.finalPoker[idx] = window.pokers[data.finalResult[idx]];
  }

  data.playerPoker = [data.finalPoker[0], data.finalPoker[1]];
  data.bankerPoker = [data.finalPoker[2], data.finalPoker[3]];
  data.playerPoint =
    data.finalPoker[0].baccaretPoint + data.finalPoker[1].baccaretPoint;
  data.bankerPoint =
    data.finalPoker[2].baccaretPoint + data.finalPoker[3].baccaretPoint;
  data.playerPoint = data.playerPoint % 10;
  data.bankerPoint = data.bankerPoint % 10;

  if (data.playerPoint < 8 && data.bankerPoint < 8) {
    let nextPoker = data.finalPoker[4];
    switch (data.playerPoint) {
      case 0:
      case 1:
      case 2:
      case 3:
      case 4:
      case 5:
        data.playerPoker.push(nextPoker);
        data.playerPoint += nextPoker.baccaretPoint;
        let playerDrawPokerPoint = nextPoker.baccaretPoint;
        data.playerPoint = data.playerPoint % 10;
        nextPoker = data.finalPoker[5];
        switch (data.bankerPoint) {
          case 0:
          case 1:
          case 2:
            data.bankerPoint += nextPoker.baccaretPoint;
            data.bankerPoker.push(nextPoker);
            data.bankerPoint = data.bankerPoint % 10;
            break;
          case 3:
            if (playerDrawPokerPoint != 8) {
              data.bankerPoint += nextPoker.baccaretPoint;
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 4:
            if ([0, 1, 8, 9].indexOf(playerDrawPokerPoint) == -1) {
              data.bankerPoint += nextPoker.baccaretPoint;
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 5:
            if ([0, 1, 2, 3, 8, 9].indexOf(playerDrawPokerPoint) == -1) {
              data.bankerPoint += nextPoker.baccaretPoint;
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
          case 6:
            if ([6, 7].indexOf(playerDrawPokerPoint) >= 0) {
              data.bankerPoint += nextPoker.baccaretPoint;
              data.bankerPoker.push(nextPoker);
              data.bankerPoint = data.bankerPoint % 10;
            }
            break;
        }
        break;
      case 6:
      case 7:
        if ([0, 1, 2, 3, 4, 5].indexOf(data.bankerPoint) >= 0) {
          data.bankerPoint += nextPoker.baccaretPoint;
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

function calcPlinko() {
  const payoutDef = {
    low8: [5.5, 1.8, 1.1, 1, 0.5, 1, 1.1, 1.8, 5.5],
    normal8: [13.4, 3, 1.2, 0.7, 0.4, 0.7, 1.2, 3, 13.4],
    high8: [30, 3.9, 1.4, 0.3, 0.2, 0.3, 1.4, 3.9, 30],
    low9: [7, 2.1, 1.4, 1, 0.7, 0.7, 1, 1.4, 2.1, 7],
    normal9: [18, 3.8, 1.6, 0.9, 0.5, 0.5, 0.9, 1.6, 3.8, 18],
    high9: [43, 6.8, 1.9, 0.6, 0.2, 0.2, 0.6, 1.9, 6.8, 43],
    low10: [9, 2.9, 1.2, 1.1, 1, 0.5, 1, 1.1, 1.2, 2.9, 9],
    normal10: [22, 5.2, 2, 1.3, 0.6, 0.4, 0.6, 1.3, 2, 5.2, 22],
    high10: [76, 10.3, 2.7, 0.9, 0.3, 0.2, 0.3, 0.9, 2.7, 10.3, 76],
    low11: [8, 2.7, 1.9, 1.2, 1, 0.7, 0.7, 1, 1.2, 1.9, 2.7, 8],
    normal11: [25, 6, 2.9, 1.7, 0.7, 0.5, 0.5, 0.7, 1.7, 2.9, 6, 25],
    high11: [120, 14, 5.1, 1.3, 0.4, 0.2, 0.2, 0.4, 1.3, 5.1, 14, 120],
    low12: [10, 2.7, 1.4, 1.3, 1.1, 1, 0.5, 1, 1.1, 1.3, 1.4, 2.7, 10],
    normal12: [36, 11, 4, 1.8, 1.1, 0.6, 0.3, 0.6, 1.1, 1.8, 4, 11, 36],
    high12: [172, 23, 7.6, 2, 0.7, 0.2, 0.2, 0.2, 0.7, 2, 7.6, 23, 172],
    low13: [9, 4.2, 3, 1.6, 1.2, 0.9, 0.7, 0.7, 0.9, 1.2, 1.6, 3, 4.2, 9],
    normal13: [48, 13, 6, 2.7, 1.3, 0.7, 0.4, 0.4, 0.7, 1.3, 2.7, 6, 13, 48],
    high13: [253, 37, 10, 4, 1, 0.2, 0.2, 0.2, 0.2, 1, 4, 10, 37, 253],
    low14: [7.1, 4, 1.6, 1.3, 1.2, 1.1, 1, 0.5, 1, 1.1, 1.2, 1.3, 1.6, 4, 7.1],
    normal14: [
      55, 14, 6.9, 3.9, 1.8, 1, 0.5, 0.2, 0.5, 1, 1.8, 3.9, 6.9, 14, 55,
    ],
    high14: [415, 52, 18, 5, 1.8, 0.3, 0.2, 0.2, 0.2, 0.3, 1.8, 5, 18, 52, 415],
    low15: [
      15, 7.4, 3, 1.9, 1.3, 1.1, 1, 0.7, 0.7, 1, 1.1, 1.3, 1.9, 3, 7.4, 15,
    ],
    normal15: [
      96, 17, 11, 4.3, 3, 1.3, 0.5, 0.3, 0.3, 0.5, 1.3, 3, 4.3, 11, 17, 96,
    ],
    high15: [
      618, 83, 24, 8, 3, 0.5, 0.2, 0.2, 0.2, 0.2, 0.5, 3, 8, 24, 83, 618,
    ],
    low16: [
      15, 9, 2, 1.5, 1.4, 1.3, 1.1, 0.9, 0.5, 0.9, 1.1, 1.3, 1.4, 1.5, 2, 9, 15,
    ],
    normal16: [
      122, 41, 10, 4.6, 3, 1.4, 1, 0.5, 0.3, 0.5, 1, 1.4, 3, 4.6, 10, 41, 122,
    ],
    high16: [
      1000, 126, 26, 8, 4, 2, 0.2, 0.2, 0.2, 0.2, 0.2, 2, 4, 8, 26, 126, 1000,
    ],
  };

  data.plinkoPayout = payoutDef[data.risk + data.rows];
  data.plinkoRows.length = 0;
  for (let i = 0; i <= data.rows; i++) {
    data.plinkoRows.push(i);
  }

  let hmacDigest0 = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":0",
    data.serverSeed
  );
  let hmacDigestBytes0 = hmacDigestToBytes(hmacDigest0);
  let hmacDigest1 = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":1",
    data.serverSeed
  );
  let hmacDigestBytes1 = hmacDigestToBytes(hmacDigest1);
  let hmacDigest2 = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":2",
    data.serverSeed
  );
  let hmacDigestBytes2 = hmacDigestToBytes(hmacDigest2);
  let hmacDigestBytes = [
    ...hmacDigestBytes0,
    ...hmacDigestBytes1,
    ...hmacDigestBytes2,
  ];

  let result = 0;
  data.plinkoPayoutIndex = "";
  for (let i = 0; i < data.rows; i++) {
    let thisResult = Math.floor(bytesToNumber(hmacDigestBytes, i * 4, 2));
    result += thisResult;
    if (data.plinkoPayoutIndex == "") {
      data.plinkoPayoutIndex = thisResult.toString();
    } else {
      data.plinkoPayoutIndex = data.plinkoPayoutIndex + " + " + thisResult;
    }
  }
  data.result = result;
  data.finalResult = data.plinkoPayout[result];
}

function calcCrash() {
  const hmacDigest = hmacSHA256(data.clientSeed, data.serverSeed);
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  const result =
    (hmacDigestBytes[0] >> 4) * Math.pow(16, 7) +
    (hmacDigestBytes[0] & 0xf) * Math.pow(16, 6) +
    (hmacDigestBytes[1] >> 4) * Math.pow(16, 5) +
    (hmacDigestBytes[1] & 0xf) * Math.pow(16, 4) +
    (hmacDigestBytes[2] >> 4) * Math.pow(16, 3) +
    (hmacDigestBytes[2] & 0xf) * Math.pow(16, 2) +
    (hmacDigestBytes[3] >> 4) * Math.pow(16, 1) +
    (hmacDigestBytes[3] & 0xf) * Math.pow(16, 0);
  data.result = result;
  data.finalResult = (4294967296 / (result + 1)) * (1 - 0.03);
}

function calcKeno() {
  let hmacDigest0 = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":0",
    data.serverSeed
  );
  let hmacDigestBytes0 = hmacDigestToBytes(hmacDigest0);
  let hmacDigest1 = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":1",
    data.serverSeed
  );
  let hmacDigestBytes1 = hmacDigestToBytes(hmacDigest1);
  let hmacDigestBytes = [...hmacDigestBytes0, ...hmacDigestBytes1];

  data.kenoCalcResult = [];
  data.kenoNumberToShuffle = [];
  data.kenoFinalResult = [];
  let currNumbers = [
    0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20,
    21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39,
  ];
  for (let i = 0; i < 10; i++) {
    data.kenoNumberToShuffle.push([...data.kenoCalcResult, ...currNumbers]);
    let currIndex = Math.floor(bytesToNumber(hmacDigestBytes, i * 4, 40 - i));
    let currNum = currNumbers[currIndex];
    data.kenoCalcResult.push(currNum);
    data.kenoFinalResult.push(currNum + 1);
    currNumbers.splice(currIndex, 1);
  }
  data.kenoNumberToShuffle.push([...data.kenoCalcResult, ...currNumbers]);
}
function calcRoulette() {
  const hmacDigest = hmacSHA256(
    data.clientSeed + ":" + data.nonce + ":0",
    data.serverSeed
  );
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  data.finalResult = Math.floor(bytesToNumber(data.hmacDigestBytes, 0, 37));
}

function hmacDigestToBytes(wordArray) {
  // Shortcuts
  var words = wordArray.words;
  var sigBytes = wordArray.sigBytes;

  // Convert
  var bytes = [];
  for (var i = 0; i < sigBytes; i++) {
    var bite = (words[i >>> 2] >>> (24 - (i % 4) * 8)) & 0xff;
    bytes.push(bite & 0xff);
  }

  return bytes;
}

function bytesToNumber(bytes, index, maxRange) {
  let resultPow =
    bytes[0 + index] / Math.pow(256, 1) +
    bytes[1 + index] / Math.pow(256, 2) +
    bytes[2 + index] / Math.pow(256, 3) +
    bytes[3 + index] / Math.pow(256, 4);
  let result = resultPow * maxRange;
  return result;
}

setTimeout(function () {
  calc();
}, 1000);
</script>

<template>
  <div class="content">
    <div class="calccontent">
      <el-form ref="form" :model="data" label-width="80px" label-position="top">
        <el-form-item label="Game">
          <el-select
            v-model="data.game"
            placeholder="Please Selece Game"
            @change="handleChange"
          >
            <el-option label="Crash" value="crash"></el-option>
            <el-option label="Dice" value="dice"></el-option>
            <el-option label="Plinko" value="plinko"></el-option>
            <el-option label="Keno" value="keno"></el-option>
            <el-option
              label="Single Baccarat"
              value="singleBaccarat"
            ></el-option>
            <el-option label="Roulette" value="roulette"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Client Seed">
          <el-input v-model="data.clientSeed" @input="handleChange"></el-input>
        </el-form-item>
        <el-form-item label="Server Seed hash" v-if="data.game == 'crash'">
          <el-input
            v-model="data.serverSeedHash"
            @input="handleChange"
          ></el-input>
        </el-form-item>
        <el-form-item label="Server Seed">
          <el-input v-model="data.serverSeed" @input="handleChange"></el-input>
        </el-form-item>
        <el-form-item label="Nonce" v-if="data.game != 'crash'">
          <el-input-number
            v-model="data.nonce"
            @change="handleChange"
            :min="1"
            label="Nonce"
          ></el-input-number>
        </el-form-item>
        <el-form-item label="Risk" v-if="data.game == 'plinko'">
          <el-select
            v-model="data.risk"
            placeholder="Please Selece Risk"
            @change="handleChange"
          >
            <el-option value="low" label="Low"></el-option>
            <el-option value="normal" label="Normal"></el-option>
            <el-option value="high" label="High"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Rows" v-if="data.game == 'plinko'">
          <el-select
            v-model="data.rows"
            placeholder="Please Selece Rows"
            @change="handleChange"
          >
            <el-option value="8" label="8"></el-option>
            <el-option value="9" label="9"></el-option>
            <el-option value="10" label="10"></el-option>
            <el-option value="11" label="11"></el-option>
            <el-option value="12" label="12"></el-option>
            <el-option value="13" label="13"></el-option>
            <el-option value="14" label="14"></el-option>
            <el-option value="15" label="15"></el-option>
            <el-option value="16" label="16"></el-option>
          </el-select>
        </el-form-item>
      </el-form>
    </div>
    <div>
      <code id="coderesult"></code>
    </div>
    <div>
      <Crash v-if="data.game === 'crash'" :data="data"></Crash>
      <Dice v-if="data.game === 'dice'" :data="data"></Dice>
      <Plinko v-if="data.game === 'plinko'" :data="data"></Plinko>
      <SingleBaccarat
        v-if="data.game === 'singleBaccarat'"
        :data="data"
      ></SingleBaccarat>
      <Keno v-if="data.game === 'keno'" :data="data"></Keno>
      <Roulette v-if="data.game === 'roulette'" :data="data"></Roulette>
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
  color: white !important;
}
</style>
