<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'
import TodoListInput from './TodoListInput.vue';
import TodoListItem from './TodoListItem.vue';

const tareasLista = ref([])

onBeforeMount(() => {
    console.log("TodoList onBeforeUnmount");
})
onMounted(() => {
    console.log("TodoList onMounted");
})
onBeforeUnmount(() => {
    console.log("TodoList onBeforeUnmount");
})
onUnmounted(() => {
    console.log("TodoList onUnmounted");
})

function onCreateTaskHandler($event){
    console.log("onCreateTaskHandler => ", $event);

    tareasLista.value.push({
        name: $event,
        done: false
    })
}
function onDoneHandler($event){
    tareasLista.value[$event].done = true
}
function onDeleteHandler($event){
    tareasLista.value.splice($event, 1)
}
</script>
<template>
    <div>
        <TodoListInput @onCreateTask="onCreateTaskHandler"></TodoListInput>
        <ul class="todolist-lista" v-if="tareasLista.length">
            <TodoListItem v-for="(tarea, index) of tareasLista" v-bind="tarea" :index="index" :key="index" @onDone="onDoneHandler" @onDelete="onDeleteHandler"></TodoListItem>
        </ul>
    </div>
</template>
<style scoped>
.todolist-lista {
    padding: 1rem;
    margin: 1rem 0;
    border: thin solid lightgrey;
    border-radius: 10px;
    list-style: none;
}
</style>