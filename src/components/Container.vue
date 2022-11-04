<template>
  <div class="container">
    <input type="text" v-model="msg" />
    <button @click="Create">Create</button>
    <TodoList :TodoLists="data" :Delete="Delete" />
  </div>
</template>

<script>
import TodoList from './ToDo.vue';
import { ref } from 'vue';
export default {
  components: {
    TodoList,
  },
  setup() {
    let data = ref([
      { name: 'eating' },
      { name: 'drinking' },
      { name: 'sleeping' },
    ]);
    function Create() {
      data.value.push({ name: this.msg });
    }
    function Delete(idx) {
      data.value.splice(idx, 1);
    }
    return {
      data,
      Create,
      Delete,
    };
  },
};
</script>

<style lang="css" scoped>
.container {
  font-size: 20px;
  display: flex;
  flex-direction: column;
  width: 60%;
  margin-left: auto;
  margin-right: auto;
}
input {
  font-size: 20px;
  border-radius: 5px;
}
button {
  border-radius: 5px;
  font-size: 20px;
  background-color: green;
}
</style>
