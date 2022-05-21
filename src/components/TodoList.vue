<script setup>
import { ref } from "vue";

const items = ref([
  { name: "書評", done: 1 },
  { name: "宇宙地球科学", done: 1 },
]);
const newTask = ref("");

const addTask = () => {
  items.value.push({ name: newTask.value, done: 1 });
};
</script>

<template>
  <div>
    <div>TodoList</div>
    <div>
      <div>未完</div>
      <div v-for="item in items" :key="item.name">
        <div v-if="item.done == 1" class="item">
          <div class="name">{{ item.name }}</div>
          <button @click="item.done = 0">done</button>
        </div>
      </div>
      <div>完</div>
      <div v-for="item in items" :key="item.name">
        <div v-if="item.done == 0" class="item">
          <div class="name">{{ item.name }}</div>
          <button @click="item.done = 2">delete</button>
        </div>
      </div>
    </div>
    <div>
      <label>
        名前
        <input v-model="newTask" type="text" />
      </label>
      <button @click="addTask">add</button>
    </div>
  </div>
</template>

<style></style>
