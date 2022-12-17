<script setup>
import Overview from './components/overview.vue'
import Implementation from './components/implementation.vue'
import Calculation from './components/calculation.vue'
import { parseQuery } from "vue-router"
import { ref } from 'vue'

let query = parseQuery(location.search)
let activeName = ref('overview')
if(query['game'] != undefined && query['game'] != "") {
  activeName = ref('calculation')
}

</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-header>Provably Fair</el-header>
      <el-main>
        <el-tabs v-model="activeName" class="tabs">
          <el-tab-pane label="Overview" name="overview">
            <Overview />
          </el-tab-pane>
          <el-tab-pane label="Implementation" name="implementation">
            <Implementation />
          </el-tab-pane>
          <el-tab-pane label="Calculation" name="calculation">
            <Calculation />
          </el-tab-pane>
        </el-tabs>
      </el-main>
      <el-footer>
        Get source 
        <a href="https://github.com/afbgamingopen/verify" target="_blank">Github.com</a>
      </el-footer>
    </el-container>
  </div>
</template>
<style scoped>
header {
  line-height: 60px;
  font-size: 50px;
}

.common-layout {
  width: 100%;
}

</style>
