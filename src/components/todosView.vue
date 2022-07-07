<template>
  <div class="container mt-3 ">
    <input
      type="text"
      class="text-center form-control"
      v-model="newTodo"
      @keypress.enter="addTodo"
      placeholder="+Add New Todo"
    />
    <transition name="switch" mode="out-in">
    <div v-if="todos.length">
      <transition-group tag="ul" name="list" appear="">
        <li
          v-for="todo in todos"
          :key="todo.id"
          @click="deleteTodo(todo.id)"
          style="cursor: pointer; height: 42px"
          class="card mt-3 fs-4 "
        >
          {{ todo.title }}
        </li>
      </transition-group>
    </div>
    <div v-else>Woohoo, nothing left todo!</div>
    </transition>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup(props, { emit }) {
    const newTodo = ref("");
    const id = Math.random();
    const todos = ref([
      { id: 1, title: "make the bed" },
      { id: 2, title: "take out the trash" },
      { id: 3, title: "do homework" },
    ]);

    const addTodo = () => {
      if (newTodo.value.length > 0) {
        const id = Math.random();
        todos.value = [{ title: newTodo.value, id }, ...todos.value];
        newTodo.value = "";
      } else {
        emit("badValue");
      }
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter(todo => todo.id != id)
    }
    return { addTodo, newTodo, todos, id ,deleteTodo };
  },
};
</script>

<style>

.list-enter-from{ opacity: 0; transform: scale(0.6);}
.list-enter-to{opacity: 1; transform: scale(1);}
.list-enter-active {transition: all 0.5s ease; }

.list-leave-active{transition: all 0.5s ease; position: absolute;}
.list-leave-from{opacity: 1; transform: scale(1);}
.list-leave-to{opacity: 0; transform: scale(0.6);}

.list-move{transition: all 0.3s ease;}

/*switch*/
.switch-enter-from, .switch-leave-to {transform: translateY(20px); opacity: 0;}
.switch-enter-to , .switch-leave-from {transform: translateY(0) ;opacity: 1;}
.switch-enter-active , .switch-leave-active  {transition: all 0.5s ease;}
</style>