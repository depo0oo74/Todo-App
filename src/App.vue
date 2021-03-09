
<template>
  <section class="todo-app">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-12 text-center">
          <h1>Todo App</h1>
        </div>
        <div class="col-md-6 text-center">
          <form @submit.prevent="addTodo()">
            <input type="text" class="form-control" v-model="todoName" placeholder="Enter what you want to do ...">
            <button v-if="todoName" type="submit" class="btn">Add</button>
          </form>
        </div>
        <div class="col-md-10">
          <table class="table">
            <tr>
              <td>todo name</td>
              <td>action</td>
            </tr>
            <tr v-for="todo in todos" :key="todo.index">
              <td style="color : #6a6af2">{{ todo }}</td>
              <td>
                <button class="btn complete">Complete</button> 
                <button class="btn remove">Remove</button>
              </td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </section>
</template>
<script>

export default {
  
  name: 'App',
  data() {
    return {
      todoName : '',
      todos : [] ,
    }
  },
  methods : {
    addTodo() {
      this.todos.push(this.todoName);
      this.todoName = ''
    },
  },
}
</script>

<style scoped>
button:focus, input:focus {
  box-shadow: none;
}
.todo-app {
  margin-top: 30px;
}
.todo-app h1 {
  background: #effe0a;
  color: #222222;
  display: inline-block;
  padding: 3px 6px;
}
.todo-app input {
  margin-top: 30px;
}
.todo-app button[type="submit"] {
  background: #effe0a;
  margin: 30px auto ;
}
.todo-app button.complete {
  background: #3ad73a;
  color: white;
  margin: auto 5px;
}
.todo-app button.remove {
  background: red;
  color: white;
}
.todo-app table {
  margin-top: 20px;
}
.todo-app td.complete {
  text-decoration: line-through;
}
</style>
