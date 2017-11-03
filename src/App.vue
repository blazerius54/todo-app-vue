<template>
  
    <div id="app">
      <!-- <router-view/> -->
      <div id='first'>
        <h2>Todos:</h2>
        <p>Completed tasks: {{todos.filter(function(todo){return todo.done === true}).length}}</p>
        <p>Pending task: {{todos.filter(todo => {return todo.done === false}).length}}</p>  
      </div>
      <div id='second'></div>
        <todo-list v-bind:todos='todos'></todo-list>
        <create-todo v-on:create-todo='addTodo'></create-todo>
      </div>
    </div>

</template>

<script>
import TodoList from '@/components/TodoList'
import CreateTodo from '@/components/CreateTodo'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo    
  },
  data() {
    return {
        todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }]
    }
  },
  methods: {
    addTodo(val) {
      this.todos.push(val)
    }
  }  
}
</script>

<style>
#app{
  display:flex;
  flex-direction: column;
}
#first{
  margin: 20px auto
}



</style>
