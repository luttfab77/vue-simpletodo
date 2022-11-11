<template>
  <div class="container">
    <Create :create="Create" />
    <TodoList :toDoes="data" :deleteItem="Delete" />
  </div>
</template>

<script>
import TodoList from './ToDo.vue';
import Create from './Create.vue';
import { ref } from 'vue';
export default {
  components: {
    TodoList,
    Create,
  },
  setup() {
    let data = ref([
      { name: 'Eating' },
      { name: 'Drinking' },
      { name: 'Sleeping' },
    ]);
    function updateDone(indx, state) {
      data.value[idx].done = state;
    }
    function Create(item) {
      data.value.push({ name: item });
    }
    function Delete(idx) {
      data.value.splice(idx, 1);
    }

    return {
      data,
      Create,
      Delete,
      updateDone,
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
  background-color: aquamarine;
}
</style>
