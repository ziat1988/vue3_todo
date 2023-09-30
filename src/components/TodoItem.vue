<script setup>    
import {ref,nextTick} from 'vue'
const props = defineProps({
  todo: String,
  index: Number
})


const isEdit = ref(false);
const inputField = ref();

const handleToogleEdit = async (e)=>{
  isEdit.value = !isEdit.value

  if(!isEdit.value){
    return
  }

  await nextTick();
  inputField.value.focus()
  
}

</script>

<template>
    <li>
      <div class="todo">
        <input 
        type="text"
        ref="inputField"
        :value="todo"
        v-if="isEdit"
        @input="$emit('update-todo',$event.target.value, index)"
        >

        <span v-else>{{todo}}</span>
      </div>
      
      <div class="todo-actions">

        <button @click="handleToogleEdit">
          Edit
        </button>
        <button @click="$emit('delete-todo',index)">
          Delete
        </button>
        
      </div>
    </li>
   
</template>

<style scoped>
li{
  display: flex;
  gap: 10px;
  padding: 16px 10px;
  background-color: #f1f1f1;
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);

}

.todo{
  flex:1;
}
</style>

