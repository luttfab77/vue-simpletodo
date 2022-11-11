<template>
  <ul>
    <li v-for="(todolist, index) in toDoes" :key="index">
      <input
        type="checkbox"
        :id="todolist.name"
        :value="index"
        v-model="checkboxes"
      />

      <span :class="{ done: remainingTasks(index) }">{{ todolist.name }}</span>
      <span
        :class="{ hideDelete: allowDelete(index) }"
        class="delete"
        @click="deleteItem(index)"
        >x</span
      >
    </li>
  </ul>
  <div class="taskInfo">
    <span> {{ doneTasks }} task(s) left </span>
    <span v-if="checkboxes.length > 0" @click="clicked" class="doneTasks">
      <a href="#">Clear {{ checkboxes.length }} completed task(s)</a>
    </span>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
export default {
  props: {
    deleteItem: {
      type: Function,
      required: true,
    },
    toDoes: {
      type: Array,
      required: true,
    },
  },
  setup(props) {
    const isDone = ref(false);
    const checkboxes = ref([]);

    function allowDelete(index) {
      console.log(checkboxes.value);
      if (checkboxes.value.includes(index)) return true;
      return false;
    }
    function clicked() {
      console.log('clicked ' + checkboxes.value);
      checkboxes.value.forEach((item) => {
        console.log(item);
        props.deleteItem(item);
        checkboxes.value = [];
        //console.log('delete: ' + props.toDoes.indexOf(item));
      });
    }
    const doneTasks = computed(() => {
      return props.toDoes.length - checkboxes.value.length;
    });
    function remainingTasks(task) {
      console.log('task: ' + task);
      if (checkboxes.value.includes(task)) return true;
      return false;
    }

    return {
      isDone,
      remainingTasks,
      checkboxes,
      clicked,
      doneTasks,
      allowDelete,
    };
  },
};
</script>

<style scope>
ul {
  list-style: none;
  flex-direction: column;
  width: 70%;
  margin: auto;
  font-family: 'Lato', sans-serif;
  font-size: 20px;
  font-weight: 400;
  font-style: italic;
}
ul li {
  margin-bottom: 10px;
  color: #5c5c5c;
  display: flex;
  margin: 5px 0;
  justify-content: space-between;
  align-content: center;
}
ul li :hover {
  opacity: 0.4;
}
.delete {
  background-color: red;
  color: white;
  padding: 0 10px;
  line-height: 1;
  border-radius: 5px;
}
.hideDelete {
  opacity: 0;
}

.done {
  text-decoration: line-through;
}
.taskInfo {
  margin-top: 15px;
  font-size: 14px;
  display: flex;
  margin-left: auto;
  color: #335c62;
  justify-self: space-between;
}
.doneTasks {
  position: absolute;
  left: 20px;
}
input[type='checkbox'] {
  width: 20px;
  background: #555;
  border-radius: 5px;
}
</style>
