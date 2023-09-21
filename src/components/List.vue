<template>
<div class="item">
  <div
    class="child"
    :class="{ 'pointer': item.children }"
    @click="updatePath(item.key);isOpen = !isOpen"
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
      :path="path"
      @pathKey="updatePath"
    />
  </template>
</div>

</template>

<script setup lang="ts">
import { toRefs, ref, watch } from 'vue'

const props = defineProps({
  item: {
    type: Object,
    default: {}
  },
  path: {
    type: Array<string>,
      default: []
  }
})

const { item, path } = toRefs(props)

const emits = defineEmits(['pathKey'])

const isOpen = ref<boolean>(false)

const updatePath = (val: string) => emits('pathKey', val)

watch(path, (val) => {
  if (val) {
    // console.log("watch path", val)
  }
}, { deep: true })

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

.highlight {
  color: yellow;
}

.icon {
  margin-right: 4px;
  font-size: 12px;
  transition: 0.3s;
}

</style>