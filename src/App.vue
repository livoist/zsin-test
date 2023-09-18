<template>
<div>
  <div class="navbar" @click.self="isOpenMenu = false">
    <div class="menuBtn" @click="isOpenMenu = true"></div>
    <SideMenu
      :isOpenMenu="isOpenMenu"
      :list="mockData"
    />
  </div>
  <div class="nineSquareContainer" @click="isOpenMenu = false">
    <NineSquare />
  </div>
</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { SideMenu, NineSquare } from '../src/components'
import { mockData } from './data'

const isOpenMenu = ref(false)

</script>

<style scoped>
.navbar {
  background: #000;
  width: 100vw;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 10px 2vw;
  box-sizing: border-box;
}

.menuBtn {
  border-top: 1px solid #fff;
  border-bottom: 1px solid #fff;
  width: 30px;
  height: 16px;
  position: relative;
  cursor: pointer;
}

.menuBtn:after {
  content: '';
  position: absolute;
  width: 100%;
  height: 1px;
  background: #fff;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.nineSquareContainer {
  width: 100vw;
  height: calc(100vh - 38px);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}
</style>