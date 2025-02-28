<script setup>
import { ref } from 'vue';

const itemList = ref([]);
const newItem = ref('');

function addItem() {
  if (!newItem.value) return;
  itemList.value.push({
    label: newItem.value,
    count: 0
  });
  newItem.value = '';
}

function decreaseCount(index) {
  if (itemList.value[index].count == 0) return;
  itemList.value[index].count = itemList.value[index].count - 1;
}

function increaseCount(index) {
  itemList.value[index].count = itemList.value[index].count + 1;
}

</script>

<template>
  <div>
    <h3>Count It</h3>
    <div style="border-bottom: 1px solid black;padding: 4px 0px;">
      <input type="text" v-model.trim="newItem" placeholder="Enter Item name" />
      <button style="margin-left: 4px;" @click="addItem">Add Item</button>
    </div>
    <div class="counter-list">
      <div v-for="(item, index) in itemList" style="padding: 4px 0px;">
        <label for="">{{ item.label }}</label>
        <button @click="decreaseCount(index)" style="margin-left: 16px;">-</button>
        <input type="number" min="0" v-model="item.count" style="margin-left: 4px;">
        <button @click="increaseCount(index)" style="margin-left: 4px;">+</button>
      </div>
      
    </div>
    
  </div>
</template>

<style scoped>
input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
input { 
    text-align: center; 
}
</style>
