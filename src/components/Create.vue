<template>
  <form @submit.prevent="doCreate">
    <div class="create">
      <input type="text" v-model="item" />
      <button @click="doCreate">Create</button>
    </div>
  </form>
</template>

<script>
import { ref } from 'vue';

export default {
  props: {
    create: {
      type: Function,
      required: true,
    },
  },
  components: {},
  setup(props) {
    const item = ref('');

    function doCreate() {
      if (item.value) {
        props.create(item.value);
        item.value = '';
      }
    }
    return {
      item,
      doCreate,
    };
  },
};
</script>

<style scoped>
input[type='text'] {
  padding: 5px;
  margin-right: 15px;
  color: #5c5c5c;
  border: 1px solid #dcdce6;
  border-radius: 8px;
}

.create {
  display: flex;
  width: 60%;
  justify-content: space-between;
  margin-bottom: 20px;
}
</style>
