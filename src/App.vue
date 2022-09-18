<script setup lang="ts">
import { app } from '@tauri-apps/api'
const i = ref(0)

let name = $ref('')
let version = $ref('')
let tauriVersion = $ref('')

;(async () => {
  name = await app.getName()
  version = await app.getVersion()
  tauriVersion = await app.getTauriVersion()
})()
</script>

<template>
  <h1
    flex="~ gap-1"
    justify-center
    items-center
    text="[var(--el-color-primary)]"
  >
    <i-ep-element-plus /> Hello Element Plus!
  </h1>

  <el-button @click="i++">Incrase: {{ i }}</el-button>

  <el-descriptions title="App">
    <el-descriptions-item label="Name">
      {{ name }}
    </el-descriptions-item>
    <el-descriptions-item label="Version">
      {{ version }}
    </el-descriptions-item>
    <el-descriptions-item label="Tauri Version">
      {{ tauriVersion }}
    </el-descriptions-item>
  </el-descriptions>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 0 30px;
}
</style>
