<script setup>
const props = defineProps({
  todos: Array,
})

</script>

<template>
<ul>
    <li v-for="todo in todos">
        {{ todo }}
        <div @click="$emit('edit-todo')">Edit</div>
    </li>
</ul>
</template>