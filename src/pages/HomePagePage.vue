<template>
    <div class="new">
      <a href="#ajouter" style="margin: 5px;">Nouvelle Tâche</a>
    </div>
  
    <div class="container">
      <table class="table" v-if="todos.length > 0">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Tâches</th>
            <th scope="col">Date</th>
            <th scope="col">Statut</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(todo, index) in todos" :key="todo.id">
            <th scope="row">{{ index + 1 }}</th>
            <td>{{ todo.title }}</td>
            <td>{{ todo.date }}</td>
            <td>{{ todo.completed ? 'Complétée' : 'En cours' }}</td>
            <td>
              <!-- Exemples de boutons d'action -->
              <button @click="modifyTodo(todo.id)">Modifier</button>
              <button class="secondary" @click="deleteTodo(todo.id)">Supprimer</button>
              <button class="contrast" @click="completeTodo(todo.id)" v-if="!todo.completed">Terminer</button>
            </td>
          </tr>
        </tbody>
      </table>
  
      <div v-else>
        <p>Aucune tâche enregistrée.</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref } from 'vue'
  
  const todos = ref([])
  
  onMounted(() => {
    todos.value = JSON.parse(localStorage.getItem('todos') || '[]')
  })
  
  // Boutons d'action (à compléter selon ton système de navigation)
  const modifyTodo = (id) => {
    window.location.hash = `#modifier:${id}`
  }
  
  const deleteTodo = (id) => {
    todos.value = todos.value.filter(todo => todo.id !== id)
    localStorage.setItem('todos', JSON.stringify(todos.value))
  }

  const completeTodo = (id) => {
  const updatedTodos = todos.value.map(todo => {
    if (todo.id === id) {
      return { ...todo, completed: true } // on met à jour "completed"
    }
    return todo
  })

  todos.value = updatedTodos
  localStorage.setItem('todos', JSON.stringify(todos.value))
}

  </script>
  
  <style>
  .table {
    margin-top: 2rem;
  }

  .table button {
    margin : .25rem;
  }
  
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
  