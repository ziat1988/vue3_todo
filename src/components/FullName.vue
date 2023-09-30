
<script setup>
    import {ref} from 'vue'
    const props = defineProps({
        firstName: String,
        lastName: String
    })

    const initText = ref(props.firstName)
    
    function displayFullName()
    {
        return `${props.firstName} ${props.lastName.toUpperCase()}`
    }

</script>


<template >
    <div class="full-name">
        {{displayFullName()}}
    </div>
    <div>
        {{ firstName }}
    </div>

    <div>
        <input type="text" v-model="initText">
        {{ initText }}
    </div>
</template>

<style scoped>
    
</style>