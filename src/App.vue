<template>
  <div class="bg-gray-600 text-white w-1/2 m-auto mt-12">
    <div class="text-center border-b-2 border-black py-4">
      <h1 class="text-3xl py-4"> Unsere Todos</h1>
      <p class="text-xl">Offene Todos: {{ todos.length }} </p>
    </div>
    <div v-for="(todo,index) in todos" :key="todo.todo">
      <TodoItem :todoprop="todo" :todoIndex="index" @toggledone-index="toggleDone" @removeTodo-index="deleteTodo"/>
    </div>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  methods: {
    toggleDone(index) {
      this.todos[index].done = !this.todos[index].done 
    },
    deleteTodo(index) {
      this.todos.splice(index,1)
    }
  },
  data() {
    return {
      todos:[
        {todo: "einkaufen", done: false},
        {todo: "sport", done: false},
        {todo: "programmieren", done: true},
        {todo: "lesen", done: false},
      ]
    }
  },
  components: {
    TodoItem
  }
}
</script>

