<template>
  <div class="todo-container">
    <span>{{ todo }}</span
    ><span v-on:click="removeTodo" class="delete">Delete</span>
  </div>
</template>

<script>
export default {
  name: "Todo",
  setup: (props, { emit }) => {
    return {
      removeTodo: () => {
        emit("remove:todo", props.index);
      },
    };
  },
  props: {
    todo: String,
    index: Number,
    name: String,
  },
};
</script>

<style scoped>
.todo-container {
  border: 1px lightgray solid;
  margin: 8px 0;
  border-radius: 6px;
  display: flex;
  justify-content: space-between;
  position: relative;
  overflow-x: hidden;
}

span {
  padding: 10px;
}

.delete {
  position: absolute;
  background-color: red;
  color: white;
  right: -66px;
  border-radius: 5px;
  transition: right ease 0.5s;
  cursor: pointer;
}

.todo-container:hover > .delete {
  right: 0px;
  display: inherit;
}
</style>
