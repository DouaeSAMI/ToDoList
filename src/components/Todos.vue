<template>
  <div>
    <h1>Todo's list</h1>
    <div>
      <form>
        <div class="form-group">
          <input type="text" v-model="title" class="form-control" placeholder="Add Task" />
        </div>
        <div class="d-grid gap-2">
          <button class="btn mb-2 btn-success" @click="addTodo()">Add Task</button>
        </div>
      </form>
      <ul class="list-group">
        <li class="list-group-item" v-bind:key="todo.id" v-for="todo in todos">
          <Todo :todo="todo" 
                 v-on:deleteTodo="deleteOneTodo()" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo.vue";
import axios from 'axios'
export default {
  components: { Todo },
  name: "Todos",
  data() {
    return {
       title:'',
       todos: [ ] 
       };
  },
  
  methods: 
  {
    deleteOneTodo(id){
      if(confirm("Are you sure you want to delete")){
        axios.delete(`http://localhost:3000/todos/${id}`)
      .then
      (() => {
         this.todos = this.todos.splice((todo) => todo.id !==id);
      });
      }
    },
    addTodo(){
      let newTodo = {
        title : this.title,
      }
      axios.post('http://localhost:3000/todos',newTodo)
      .then(response => console.log(response.data))
    },
    getTodos(){
      axios.get('http://localhost:3000/todos')
      .then(response => this.todos = response.data)
    }
  },
  created(){
    this.getTodos();
  }
};

</script>

<style></style>
