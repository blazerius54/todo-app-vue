<template>
  <div>
    <p>Completed tasks: {{todos.filter(function(todo){return todo.done === true}).length}}</p>
    <p>Pending task: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    
    <todo v-for="todo in todos" v-bind:todo="todo" v-on:delete-todo="deleteTodo"></todo>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo'

export default {
    components: {
        Todo
    },
    props:['todos'],
    data() {
        return {

        }
    },
    methods: {
        deleteTodo(todo) {
            const index = this.todos.indexOf(todo);
            this.todos.splice(index,1)
        }
    }
};
</script>
<style>
</style>