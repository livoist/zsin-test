<template>
<div class="container">
  <div
    v-for="n in 9"
    class="square"
    :class="[
      { 'h-gap': n === 2 || n === 5 || n === 8 },
      { 'v-gap': n === 4 || n === 5 || n === 6 }
    ]"
  >
    <div class="square-bg" :class="{ 'an-shine': n === 3 || n === 5 || n === 9 }"></div>
    <div v-if="n === 1 || n === 3 || n === 7 || n === 9" class="ball">B</div>
  </div>
</div>
</template>

<script setup lang="ts"></script>

<style scoped>
@media (min-width: 390px) {
  .container {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
  }

  .square {
    position: relative;
    width: 32.3333%;
    height: 32.3333vw;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    border: 2px solid #000;
    box-sizing: border-box;
  }

  .square-bg {
    position: relative;
    background: radial-gradient(circle, rgba(113,81,95,1) 81%, rgba(0,0,0,1) 100%);
    width: 100%;
    height: 100%;
    z-index: 1;
  }

  .h-gap {
    margin: 0 1.5vw;
  }

  .v-gap {
    margin-top: 1.5vw;
    margin-bottom: 1.5vw;
  }

  .ball {
    width: 30px;
    height: 30px;
    background: #A5F12B;
    border-radius: 50%;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    justify-content: center;
    align-items: center;
    color: #000;
    z-index: 2;
    animation: move 2s both infinite;
  }

  .an-shine {
    animation: shine both 1s infinite alternate;
  }
}

@keyframes shine {
  0% {
    opacity: 100%;
  }
  100% {
    opacity: 60%;
  }
}

@keyframes move {
  0% {
    transform: translate(-50%, -50%);
  }
  100% {
    transform: translateX(100vw);
  }
}

</style>