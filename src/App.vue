<template>
  <div id="app">
    <div class="container">
      <h2>{{ title }}</h2>
      <AddTodo></AddTodo>
      <!-- <MyTodos></MyTodos> -->
    </div>
  </div>
</template>

<script>
import addtodos from "./components/AddTodos.vue";
import mytodos from "./components/mytodo.vue";

export default {
  components: {
    AddTodo: addtodos,
    MyTodos: mytodos,
  },

  name: "app",

  data() {
    return {
      title: "Todo App",
    };
  },

  methods: {},
};
</script>

<style scoped>
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.6;
  background: #e8f7f0;
}

.container {
  max-width: 1200px;
  margin: auto;
  overflow: auto;
  padding: 0 2rem;
}
</style>
