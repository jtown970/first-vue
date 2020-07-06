<template>
  <div class="container">
    <div class="row">
      <div class="col">

        
      </div>
    </div>
    <div class="row">
      <NewTodo @on-addtodo="addTodo($event)"/>
    </div>
    <div class="row">
      <div class="col">
        <ul class="list-group">
          <Todo v-for="(todo, index) in todos" :key="index"
          :todoString="todo.todoString"
          :completed="todo.completed"
          @on-delete="deleteTodo(todo)"
          @on-toggle="toggleTodo(todo)"
          @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
// this is where and how to import 
import Todo from "./Todo"
import NewTodo from "./NewTodo"
export default{
  // must put components that will be used in here
  components:{
    Todo,
    NewTodo
  },
  // can think of data like state
  data(){ 
    return {
      todos: [
        {todoString: 'learn vue', completed: false},
        {todoString: 'make a todo list with vue', completed: false},
        {todoString: 'show class my todo list using vue', completed: false}
      ]
    }
  },
  methods: {
    addTodo(newTodo){
      this.todos.push({
        todoString: newTodo,
        completed: false
      });
    },
    toggleTodo(todo){
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString){
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo){
      this.todos = this.todos.filter( 
        todo => todo.todoString  !== deleteTodo.todoString);
    }
  }
}
</script>

<style>

</style>