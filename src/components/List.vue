<template>
<div class="item">
  <div
    class="child"
    :class="{ 'pointer': item.children }"
    @click="isOpen = !isOpen"
  >
    <span v-if="item.children" class="icon">
      {{ isOpen ? '▼' : '▶︎' }}
    </span>
    <p>{{ item.text }}</p>
  </div>
  <template v-if="item.children">
    <List
      v-show="isOpen"
      class="subMenu"
      v-for="child in item.children"
      :item="child"
    />
  </template>
</div>

</template>

<script setup lang="ts">
import { toRefs, ref } from 'vue'

const props = defineProps({
  item: {
    type: Object,
    default: {}
  }
})

const { item } = toRefs(props)
const isOpen = ref<boolean>(false)

</script>

<style scoped>
.item {
  padding: 10px 20px;
}

.subMenu {
  padding-left: 30px;
}

.child {
  display: flex;
  align-items: center;
  white-space: nowrap;
}

.child.pointer {
  cursor: pointer;
}

.icon {
  margin-right: 4px;
  font-size: 12px;
  transition: 0.3s;
}

</style>