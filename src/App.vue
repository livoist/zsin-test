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
    <div class="btnContainer">
      <div class="cssControl">
        <p>extra case2:<br />balls animation mode</p>
        <div class="btns">
          <button
            :class="{ 'active': ballAnModeIsNormal && !isJSAnimation }"
            :disabled="isJSAnimation"
            @click="ballAnModeIsNormal = true"
          >normal</button>
          <button
            :class="{ 'active': !ballAnModeIsNormal }"
            :disabled="isJSAnimation"
            @click="ballAnModeIsNormal = false"
          >all to center</button>
        </div>
      </div>

      <div class="jsControl">
        <p>extra case1:<br />use JS draw ballsToCenter animation</p>
        <button :disabled="!ballAnModeIsNormal" @click="isJSAnimation = !isJSAnimation">
          {{ isJSAnimation ? 'clear JS all to center' : 'all to center' }}
        </button>
      </div>
    </div>
    <NineSquare
      :ballAnModeIsNormal="ballAnModeIsNormal"
      :isJSAnimation="isJSAnimation"
    />
  </div>
</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { SideMenu, NineSquare } from '../src/components'
import { mockData } from './data'

const isOpenMenu = ref(false)
const ballAnModeIsNormal = ref<boolean>(true)
const isJSAnimation = ref<boolean>(false)

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
  flex-direction: column;
}

.btnContainer {
  text-align: center;
  position: absolute;
  top: 7%;
  font-size: 14px;
}

.btnContainer p {
  margin-bottom: 10px;
}

.btns {
  display: flex;
  justify-content: center;
  align-items: center;
}

.btns button {
  margin: 0 4px;
}

.cssControl {
  margin-bottom: 20px;
}

.active {
  background: #000;
  color: #fff;
}
</style>