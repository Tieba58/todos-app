<template>
    <div class="new">
        <a href="#" style="margin: 5px;">Retour</a>
    </div>
    <h1>Nouvelle Tâche</h1>
    <div v-if="state === 'error'"> Imoossible d'enregistrer les données</div>
    <div v-else :aria-busy="state === 'loading'">
        <div class="container">
            <ToDoForm :todo="todo" type="Modifier" />
        </div>
    </div>
</template>

<script setup>
import ToDoForm from '@/components/ToDoForm.vue';
import { ref } from 'vue';

const state = ref('idle')
const todo = ref({
    title: '',
    body: '',
    date: ''
})
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