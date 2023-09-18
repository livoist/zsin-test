<template>
<div class="menu" :class="{ 'isOpenMenu': isOpenMenu }">
  <div class="menu-bg"></div>
  <div class="menu-list">
    <List v-for="item in list" :item="item" />
  </div>
</div>
</template>

<script setup lang="ts">
import { toRefs } from 'vue'
import List from './List.vue'
import { type ListItem } from '../type'

const props = defineProps({
  isOpenMenu: {
    type: Boolean,
    default: false
  },
  list: {
    type: Array<ListItem>,
    default: []
  }
})

const { isOpenMenu, list } = toRefs(props)

</script>

<style scoped>
@media (min-width: 390px) {
  .menu {
    transition: 0.3s;
    width: 50vw;
    height: 100vh;
    position: fixed;
    right: 0;
    top: 0;
    transform: translateX(100%);
    z-index: 10;
  }
  .menu-bg {
    background: rgba(0, 0, 0,0.8);
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }

  .menu-list {
    position: relative;
    z-index: 1;
    color: #fff;
    overflow-y: scroll;
    height: 100%;
  }

  .menu.isOpenMenu {
    transform: translateX(0%);
    right: 0;
  }
}
</style>