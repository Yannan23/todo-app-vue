<script setup>
import { ref } from 'vue';

const str = ref('');
const list = ref([
  {
    isCompleted: false,
    text: 'Learn Vue 3'
  },
  {
    isCompleted: false,
    text: 'Learn Vue Router'
  },
  {
    isCompleted: false,
    text: 'Learn Vuex'
  }
]);
const checkbox = ref(false);

const isCompleted = () => {
  isCompleted.value = !isCompleted.value;
};

const add = () => {
  list.value.push({
    isCompleted: false,
    text: str.value
  });
  str.value = '';
};

function del(index) {
  list.value.splice(index, 1);
}

</script>

<template>
  <h1>Todo App</h1>
  <form id="form">
    <div class="form-control">
      <input v-model="str" type="text" placeholder="Enter your todo" id="input" autocomplete="off" class="input">
      <div @click="add" class="todo-button">Add Todo</div>
    </div>
    <div v-for="item in list" :class="item.isCompleted ? 'completed' : 'item'" class="todo">
      <div>
        <input @click="isCompleted" v-model="item.isCompleted" type="checkbox" id="checkbox">
        <span>{{ item.text }}</span>
      </div>
      <div class="del" @click="del">delete</div>
    </div>
  </form>
</template>
