<template>
  <div class="todos">
    <h1>Lista de Tarefas</h1>

    <ul>
      <li v-for="todo in todos" :key="todo.identify">
        {{ todo.name }}
      </li>
    </ul>

    <input type="text" v-model="name" />
  </div>
</template>

<script>
import { onMounted } from "vue";
import TodoService from "@/services/todos.service";

export default {
  name: "TodosView",
  setup() {
    onMounted(() => {
      TodoService.getAll()
        .then((response) => {
          console.log(response);
        })
        .catch((error) => console.log(error));
    });
  },
};
</script>
