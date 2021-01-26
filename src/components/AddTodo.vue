<template>
    <div>
        <!-- on submit call addTodo method and then pass on to App.vue -->
        <form @submit="addTodo">
            <!-- to pass input value to state, use v-model -->
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddTodo",
    data() {       //making a initial state for the input text and set it to title
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                id: uuidv4(),    //if using json placeholder api, it automatically assign id so we don't need uuid
                title: this.title,
                completed: false
            }
            // after obj constructed, send to parent, call it add-todo
            this.$emit('add-todo', newTodo)

            this.title = '';
        }
    }
}
</script>

<style  scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>