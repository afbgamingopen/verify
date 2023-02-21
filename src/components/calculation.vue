<script setup>
import { reactive } from 'vue'
import { parseQuery } from "vue-router"
import hmacSHA256 from 'crypto-js/hmac-sha256';

import Dice from './dice.vue'
import Plinko from './plinko.vue'
import SingleBaccarat from './singleBaccarat.vue'

let query = parseQuery(location.search);

const data = reactive({
    game: query['game']?query['game']:'',
    clientSeed: query['clientSeed']?query['clientSeed']:'',
    serverSeed: query['serverSeed']?query['serverSeed']:'',
    nonce: query['nonce']?query['nonce']:1,
    cursor: 0,
    risk: query['risk']?query['risk'].toLowerCase():'normal',
    rows: query['rows']?query['rows']:16,

    result: 0,
    finalResult: '',
    hmacDigest: '',
    hmacDigestBytes: [],

    plinkoPayout: [],
    plinkoRows: [],
    plinkoPayoutIndex: '',
})

function handleChange() {
   calc();
}

function calc() {
    if(data.game == "dice") {
      calcDice();
    }else if(data.game == "singleBaccarat") {
      calcSingleBaccarat();
    }else if(data.game == "plinko") {
      calcPlinko();
    }
}

function calcDice() {
    const hmacDigest = hmacSHA256(data.clientSeed+":"+data.nonce+":0", data.serverSeed);
    const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
    data.hmacDigest = hmacDigest;
    data.hmacDigestBytes = hmacDigestBytes;
    data.finalResult = (Math.floor(bytesToNumber(data.hmacDigestBytes, 0, 10001))/100);
}

function calcSingleBaccarat() {
  const hmacDigest = hmacSHA256(data.clientSeed + ":" + data.nonce + ":0", data.serverSeed);
  const hmacDigestBytes = hmacDigestToBytes(hmacDigest);
  data.hmacDigest = hmacDigest;
  data.hmacDigestBytes = hmacDigestBytes;
  data.result = [0, 0, 0, 0, 0, 0];
  data.finalResult = [0, 0, 0, 0, 0, 0];
  data.finalPoker = [0, 0, 0, 0, 0, 0];
  for (let idx = 0; idx < 6; idx++) {
    data.result[idx] = bytesToNumber(data.hmacDigestBytes, idx*4, 52);
    data.finalResult[idx] = (Math.floor(data.result[idx]));
    data.finalPoker[idx] = window.pokers[data.finalResult[idx]];
  }

  data.playerPoker = [data.finalPoker[0], data.finalPoker[1]];
  data.bankerPoker = [data.finalPoker[2], data.finalPoker[3]];
  data.playerPoint = data.finalPoker[0].baccaretPoint + data.finalPoker[1].baccaretPoint
  data.bankerPoint = data.finalPoker[2].baccaretPoint + data.finalPoker[3].baccaretPoint
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
        let playerDrawPokerPoint = nextPoker.baccaretPoint;
        data.playerPoint = data.playerPoint % 10;
        nextPoker = data.finalPoker[5];
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

function calcPlinko() {
  const payoutDef = {
    low8:     [5.6,	2.1,	1.1,	1,	0.5,	1,	1.1,	2.1,	5.6],
    normal8:  [13,	3,	1.3,	0.7,	0.4,	0.7,	1.3,	3,	13],
    high8:    [29,	4,	1.5,	0.3,	0.2,	0.3,	1.5,	4,	29],
    low9:     [5.6,	2,	1.6,	1,	0.7,	0.7,	1,	1.6,	2,	5.6],
    normal9:  [18,	4,	1.7,	0.9,	0.5,	0.5,	0.9,	1.7,	4,	18],
    high9:    [43,	7,	2,	0.6,	0.2,	0.2,	0.6,	2,	7,	43],
    low10:     [8.9,	3,	1.4,	1.1,	1,	0.5,	1,	1.1,	1.4,	3,	8.9],
    normal10:  [22,	5,	2,	1.4,	0.6,	0.4,	0.6,	1.4,	2,	5,	22],
    high10:    [76,	10,	3,	0.9,	0.3,	0.2,	0.3,	0.9,	3,	10,	76],
    low11:     [8.4,	3,	1.9,	1.3,	1,	0.7,	0.7,	1,	1.3,	1.9,	3,	8.4],
    normal11:  [24,	6,	3,	1.8,	0.7,	0.5,	0.5,	0.7,	1.8,	3,	6,	24],
    high11:    [120,	14,	5.2,	1.4,	0.4,	0.2,	0.2,	0.4,	1.4,	5.2,	14,	120],
    low12:     [10,	3,	1.6,	1.4,	1.1,	1,	0.5,	1,	1.1,	1.4,	1.6,	3,	10],
    normal12:  [33,	11,	4,	2,	1.1,	0.6,	0.3,	0.6,	1.1,	2,	4,	11,	33],
    high12:    [170,	24,	8.1,	2,	0.7,	0.2,	0.2,	0.2,	0.7,	2,	8.1,	24,	170],
    low13:     [8.1,	4,	3,	1.9,	1.2,	0.9,	0.7,	0.7,	0.9,	1.2,	1.9,	3,	4,	8.1],
    normal13:  [43,	13,	6,	3,	1.3,	0.7,	0.4,	0.4,	0.7,	1.3,	3,	6,	13,	43],
    high13:    [260,	37,	11,	4,	1,	0.2,	0.2,	0.2,	0.2,	1,	4,	11,	37,	260],
    low14:     [7.1,	4,	1.9,	1.4,	1.3,	1.1,	1,	0.5,	1,	1.1,	1.3,	1.4,	1.9,	4,	7.1],
    normal14:  [58,	15,	7,	4,	1.9,	1,	0.5,	0.2,	0.5,	1,	1.9,	4,	7,	15,	58],
    high14:    [420,	56,	18,	5,	1.9,	0.3,	0.2,	0.2,	0.2,	0.3,	1.9,	5,	18,	56,	420],
    low15:     [15,	8,	3,	2,	1.5,	1.1,	1,	0.7,	0.7,	1,	1.1,	1.5,	2,	3,	8,	15],
    normal15:  [88,	18,	11,	5,	3,	1.3,	0.5,	0.3,	0.3,	0.5,	1.3,	3,	5,	11,	18,	88],
    high15:    [620,	83,	27,	8,	3,	0.5,	0.2,	0.2,	0.2,	0.2,	0.5,	3,	8,	27,	83,	620],
    low16:     [16,	9,	2,	1.4,	1.4,	1.2,	1.1,	1,	0.5,	1,	1.1,	1.2,	1.4,	1.4,	2,	9,	16],
    normal16:  [110,	41,	10,	5,	3,	1.5,	1,	0.5,	0.3,	0.5,	1,	1.5,	3,	5,	10,	41,	110],
    high16:    [1000,	130,	26,	9,	4,	2,	0.2,	0.2,	0.2,	0.2,	0.2,	2,	4,	9,	26,	130,	1000],
  };

  data.plinkoPayout = payoutDef[data.risk+data.rows];
  data.plinkoRows.length = 0;
  for(let i = 0; i <= data.rows; i++) {
    data.plinkoRows.push(i);
  }
  
  let hmacDigest0 = hmacSHA256(data.clientSeed+":"+data.nonce+":0", data.serverSeed);
  let hmacDigestBytes0 = hmacDigestToBytes(hmacDigest0);
  let hmacDigest1 = hmacSHA256(data.clientSeed+":"+data.nonce+":1", data.serverSeed);
  let hmacDigestBytes1 = hmacDigestToBytes(hmacDigest1);
  let hmacDigest2 = hmacSHA256(data.clientSeed+":"+data.nonce+":2", data.serverSeed);
  let hmacDigestBytes2 = hmacDigestToBytes(hmacDigest2);
  let hmacDigestBytes = [...hmacDigestBytes0, ...hmacDigestBytes1, ...hmacDigestBytes2];

  let result = 0;
  data.plinkoPayoutIndex = '';
  for(let i = 0; i < data.rows; i++) {
    let thisResult = (Math.floor(bytesToNumber(hmacDigestBytes, i*4, 2))); 
    result += thisResult;
    if(data.plinkoPayoutIndex == ''){
      data.plinkoPayoutIndex = thisResult.toString();
    }else{
      data.plinkoPayoutIndex = data.plinkoPayoutIndex + ' + ' + thisResult;
    }
  }
  data.result = result;
  data.finalResult = data.plinkoPayout[result]
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

function bytesToNumber(bytes, index, maxRange) {
  let resultPow = bytes[0+index]/Math.pow(256,1) + 
          bytes[1+index]/Math.pow(256,2) +
          bytes[2+index]/Math.pow(256,3) +
          bytes[3+index]/Math.pow(256,4);
  let result = resultPow * maxRange;
  return result;
}

setTimeout(function() { calc(); }, 1000);

</script>

<template>
  <div class="content">
    <div class="calccontent">
        <el-form ref="form" :model="data" label-width="80px" label-position="top">
            <el-form-item label="Game">
              <el-select v-model="data.game" placeholder="Please Selece Game" @change="handleChange">
                <el-option label="Dice" value="dice"></el-option>
                <el-option label="Plinko" value="plinko"></el-option>
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
            <el-form-item label="Risk" v-if="data.game=='plinko'" >
              <el-select v-model="data.risk" placeholder="Please Selece Risk" @change="handleChange">
                <el-option value="low" label="Low"></el-option>
                <el-option value="normal" label="Normal"></el-option>
                <el-option value="high" label="High"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Rows" v-if="data.game=='plinko'" >
              <el-select v-model="data.rows" placeholder="Please Selece Rows" @change="handleChange">
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
      <code id="coderesult">
      </code>
    </div>
  <div>
    <Dice v-if="data.game==='dice'" :data="data" ></Dice>
    <Plinko v-if="data.game==='plinko'" :data="data" ></Plinko>
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
