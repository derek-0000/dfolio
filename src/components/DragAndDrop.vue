<script>
import { ref } from "vue";
export default {
  setup() {
    const items = ref([
      { id: 0, title: "Item1", list: 1 },
      { id: 1, title: "Item2", list: 1 },
      { id: 2, title: "Item3", list: 2 },
    ]);
    const getList = (list) => {
      return items.value.filter((item) => item.list == list);
    };

    const startDrag = (event, item) => {
        console.log(item)
        event.dataTransfer.dropEffect = 'move'  
        event.dataTransfer.effectAllowed = 'move'
        event.dataTransfer.setData('itemId', item.id)
     }

     const onDrop = (event, list) =>{
        const itemId = event.dataTransfer.getData('itemId')
        const item = items.value.find((item)=> item.id == itemId)
        item.list = list
     }

    return {
      getList,
      startDrag,
      onDrop
    };
  },
};
</script>

<template>
  <div class="drop-zone" @drop="onDrop($event, 1)" @dragenter.prevent @dragover.prevent>
    <div v-for="item in getList(1)" :key="item.id" class="drag-el" draggable="true" @dragstart="startDrag($event, item)" >
      {{ item.title }}
    </div>
  </div>
  <div class="drop-zone" @drop="onDrop($event, 2)" @dragenter.prevent @dragover.prevent>
    <div v-for="item in getList(2)" :key="item.id" class="drag-el" draggable="true" @dragstart="startDrag($event, item)" >
      {{ item.title }}
    </div>
  </div>
</template>

<style>
.drop-zone {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 2rem;
  padding: 1rem;
  width: 50%;
  background-color: var(--var-soft-pink);
  color: var(--var-default-gray);
  min-height: 1rem;
  border: 1px solid white;
}
.drag-el {
  background-color: var(--var-soft-pink-strong);
  margin: 0.5rem;
}
</style>
