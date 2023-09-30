
<script setup>
    import { ref, defineEmits,nextTick } from 'vue';
    
    const emit = defineEmits(['create-todo'])
    const todo = ref('');
    const isValid = ref(true);
    const errorMsg = ref('');
    const inputRef = ref();

    const submitForm = (event)=>
    {
       event.preventDefault();
       if(todo.value.trim() === ""){
        errorMsg.value= "Field can not empty"
        isValid.value = false; 
        
        nextTick(()=>{
            inputRef.value.focus()
        })
        return;
       } 
     
       emit('create-todo', todo.value)
       todo.value= ""
       isValid.value=true

    }

</script>

<template lang="">
    <div>
        <form @submit="submitForm">
            <input ref="inputRef" type="text" v-model="todo">
            <button type="submit"> ADD </button>
        </form>
    </div>

    <div v-if="!isValid">{{errorMsg}}</div>
</template>