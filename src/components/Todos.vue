<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <!-- <h3>{{todo.title}}</h3> -->
            <!--  1. passing the looped todo to TodoItem -->
            <!--  2. inheriting the delete click from TodoItem, then pass it above to App.vue -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>    
</template>

<script>

import TodoItem from './TodoItem';

export default {
    name: "Todos",    
    components: {
        TodoItem
    },
    props: ["todos"]  //props passed from the state App.vue, to loop use v-for

}
</script>  

<style scope>  

</style>