<template>
  <div>
    <todo v-for="todo in todos" v-bind:todo="todo" v-on:delete-todo="deleteTodo" v-on:complete-todo='completeTodo'></todo>
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
        },
        completeTodo(todo) {
            const index = this.todos.indexOf(todo);
            
            this.todos[index].done = true;       
        }
    }
};
</script>
<style>
</style>