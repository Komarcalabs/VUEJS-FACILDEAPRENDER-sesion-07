<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted, useTemplateRef } from 'vue'

const emit = defineEmits(["onCreateTask"])

const tarea = ref("")

const input = useTemplateRef("input")

function agregarTarea(){
    console.log("Funcion agregarTarea => ", tarea.value);
    emit("onCreateTask", tarea.value)
    tarea.value = ""
}

onBeforeMount(() => {
    console.log("TodoListInput onBeforeUnmount");
})
onMounted(() => {
    console.log("TodoListInput onMounted");
    input.value.focus()
})
onBeforeUnmount(() => {
    console.log("TodoListInput onBeforeUnmount");
})
onUnmounted(() => {
    console.log("TodoListInput onUnmounted");
})
</script>
<template>
    <form @submit.prevent="agregarTarea">
        <div class="todolist-input">
            <input type="text" v-model="tarea" ref="input">
            <button>Agregar Tarea</button>
        </div>
    </form>
</template>
<style scoped>
.todolist-input {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 1rem;
    padding: 1rem;
    border: thin solid lightgray;
    border-radius: 10px;
}
</style>