<template>
  <div>
    <draggable v-model="targetList"
                group="targetList"
                item-key="id"
                handle=".list-item-handle"
                drag-class="list-item-ghost"
    >
      <template #item="{element}">
        <div class="list-item">
          <input type="checkbox" class="list-item-checkbox">
          <span class="list-item-text">{{ element.name }}</span>
          <span v-if="element.canEdit" class="list-item-button">✏</span>
          <span class="list-item-handle list-item-button">三</span>
        </div>
      </template>
    </draggable>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import draggable from 'vuedraggable'

export default defineComponent({
  name: 'pageFive',
  components: { draggable },
  setup () {
    const targetList = ref([
      { id: '1', name: '생활비', canEdit: false },
      { id: '2', name: '투자', canEdit: false },
      { id: '3', name: '급여', canEdit: false },
      { id: '4', name: '여가', canEdit: false },
      { id: '5', name: '저축', canEdit: false },
      { id: '6', name: '사업', canEdit: false },
      { id: '7', name: '공과금', canEdit: true },
      { id: '8', name: '쇼핑', canEdit: true }
    ])

    return { targetList }
  }
})
</script>

<style lang="scss" scoped>
.list-item {
  display: flex;
  gap: 10px 0;
  align-items: center;
  padding: 0 30px;
  font-size: 16px;
}
.list-item-ghost {
  background: yellow;
}
.list-item-checkbox {
  transform: scale(1.25);
  margin-right: 5px;
}
.list-item-text {
  margin-right: auto;
}
.list-item-button {
  cursor: pointer;
  padding: 5px;
}
</style>
