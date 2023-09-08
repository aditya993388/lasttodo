
<template>
  <div class="todo-app custom-todo-app">
    <h1>Todo App</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" class="input-field" placeholder="Add a task">
    <ul>
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <span class="custom-todo-item">{{ todo.text }}</span>
        <button @click="deleteTodo(index)" class="custom-delete-button">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.custom-todo-app {
  font-family: 'Verdana', sans-serif; 
  max-width: 50%;
  max-height: 50%; 
  margin: 0 0;
  padding: 2rem; 
  background-color: #6edda9; 
  border-radius: 20px; 
  text-align: center;
}

h1 {
  font-size: 48px; 
  margin-top: 10px;
  margin-bottom: 30px; 
  color: #333;
}

ul {
  list-style-type: circle;
  padding: 1 rem;
 
}

.custom-todo-item { 
  margin-bottom: 20px; 
  font-size: 1.5rem; 
  margin-top: 1rem;
  margin-bottom: 1.7rem;
  margin-right: 3rem;
}

.custom-delete-button {
  background-color: #858180; 
  color: #fff;
  border: none;
  padding: 5px 9px; 
  cursor: pointer;
  font-size: 16px; 
  margin-top: -1rem;
}

.custom-delete-button:hover {
  background-color: #CD5C5C; 
}
</style>