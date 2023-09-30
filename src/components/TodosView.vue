<script setup>
import {reactive} from 'vue'
import TodoInput from './TodoInput.vue';
import TodoItem from './TodoItem.vue';

const todoState = reactive({
    todos:[]
});
const handleCreateTodo = (todo)=>{
    todoState.todos.push(todo)
}

const handleUpdateTodo= (todo,index)=>{
    todoState.todos[index] = todo
    console.log(todo,index)
}

const handleDeleteTodo = (index)=>{
    todoState.todos.splice(index,1)
}

</script>

<template>
    <main>
    <h2>My Todo</h2>
    <TodoInput @create-todo="handleCreateTodo"/>

    <div class="wrapper-todo-list">
        <ul class="todo-list">
            <TodoItem
            v-for="(todo, index) in todoState.todos"
            :todo="todo"
            :index="index"
            @update-todo="handleUpdateTodo"
            @delete-todo="handleDeleteTodo"
            />
        </ul>
    </div>
</main>
</template>

<style scoped>
main{
    display: flex;
    flex-direction: column;
    max-width: 500px;
    width: 100%;
    margin: 0 auto;
    padding: 40px 16px;
}

 .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

</style>