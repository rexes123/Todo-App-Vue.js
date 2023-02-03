

<!-- Todo Form -->

<!-- Todo List -->
<template>
  <h1>Vue Todo App</h1>
  <form>
<label>Enter your todo:</label>
<!-- v-model is two way binding-->
<input v-model="todoInput" type="text" placeholder="Enter here...">
<button @click.prevent="addTodo()">Add Todo</button>
</form>

<!-- {{ todoInput }} -->
<ul>
  <!-- todo in todos array -->
  <li :key="todo.id" v-for="todo in todos">
    <span :class= "{ completedTodo: todo.completed }">{{ todo.item }}</span>
    <button @click.prevent="completedTodo(todo)">
      {{ todo.completed ? 'Undo' : 'Completed'}}
    </button>
    <button @click.prevent="deleteTodo(todo.id)">Delete</button>
  </li>
  <!-- todo item -->
</ul>

<!-- {{ generateID() }} -->

</template>


<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
export default{
  name: 'TodoApp',
  data(){
    return {
      todoInput: '',
      todos: [],
    };
  },

  methods: {
    generateID(){
       const randomID = new Date().valueOf();

      return randomID;
     },
    addTodo(){
       const newTodo ={
         id: this.generateID(),
         item: this.todoInput,
         completed: false,
       };

       this.todos.push(newTodo);
       this.todoInput = '';
    },
    deleteTodo(todoID){
      this.todos = this.todos.filter((todo) => todo.id !== todoID);
    },
    completedTodo(todo){
      todo.completed = !todo.completed;
    },
  },
};
</script>

<style>
.completedTodo{
  color: blue;
  text-decoration: line-through;
}

</style>
