<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'
const {index} = defineProps({
    name: String,
    index: Number,
    done: Boolean,
})

const emit = defineEmits(["onDone","onDelete"])


onBeforeMount(() => {
    console.log("TodoListItem onBeforeMount");
})
onMounted(() => {
    console.log("TodoListItem onMounted");
})
onBeforeUpdate(() => {
    console.log("TodoListItem onBeforeUpdate");
})
onUpdated(() => {
    console.log("TodoListItem onUpdated");
})
onBeforeUnmount(() => {
    console.log("TodoListItem onBeforeUnmount");
})
onUnmounted(() => {
    console.log("TodoListItem onUnmounted");
})

function marcar(){
    emit("onDone", index)
}
function borrar(){
    emit("onDelete", index)
}
</script>
<template>
    <li class="todolist-item">
        <p class="nombre" :class="{'nombre--done': done}">{{ name }}</p>
        <button class="button button--marcar" @click="marcar" v-if="!done">Marcar</button>
        <button class="button button--borrar" @click="borrar">Borrar</button>
    </li>
</template>
<style scoped>
.todolist-item {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 1rem;
}
.nombre {
    font-size: 1.25rem;
    font-weight: 600;
    color: white;
}
.nombre--done {
    text-decoration: line-through;
    text-decoration-color: green;
    text-decoration-thickness: 3px;
}
.button {
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 15px;
    border: thin solid;
}
.button--marcar {
    background-color: green;
    border-color: green;
}
.button--borrar {
    background-color: red;
    border-color: red;
}
</style>