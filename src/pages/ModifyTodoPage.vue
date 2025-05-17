<template>
    <div class="new">
        <a href="#" style="margin: 5px;">Retour</a>
    </div>
    <h1>Modifier Tâche</h1>
    <div v-if="state === 'error'">Impossible de modifier les données</div>
    <div v-else :aria-busy="state === 'loading'">
        <div class="container">
            <ToDoForm :todo="todo" :on-save="updateTodo" type="Modifier" />
        </div>
    </div>
</template>

<script setup>
import ToDoForm from '@/components/ToDoForm.vue';
import { ref } from 'vue';

const props = defineProps({
    id: String,
})

const state = ref('idle')

// Charger tous les todos depuis localStorage
const todos = ref(JSON.parse(localStorage.getItem('todos') || '[]'))

// Trouver la tâche à modifier
const todo = ref(
    todos.value.find(t => t.id == props.id) || {
        title: '',
        body: '',
        date: '',
    }
)

// Fonction pour mettre à jour la tâche
const updateTodo = (updatedTodo) => {
    state.value = 'loading'

    const index = todos.value.findIndex(t => t.id == props.id)
    if (index !== -1) {
        todos.value[index] = { ...updatedTodo, id: props.id }
        localStorage.setItem('todos', JSON.stringify(todos.value))
        state.value = 'idle'
    } else {
        state.value = 'error'
    }
}
</script>

<style>
.new {
    margin-top: 2rem;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

.new a {
    border: 0.15rem rgba(104, 104, 220, 0.789) solid;
    border-radius: 1rem;
    padding: 1rem;
    color: blue;
    text-decoration: none;
}

.new a:hover {
    background-color: rgba(104, 104, 220, 0.789);
    color: wheat;
}
</style>