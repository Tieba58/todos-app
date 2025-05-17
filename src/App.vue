<template>
  <Header />
  <div class="container">
    <AddTodoPage v-if="page === 'ajouter'" />
    <ModifyTodoPage v-else-if="page === 'modifier'" :id="param" />
    <HomePage v-else-if="page == ''" />
    <NotFoundPage v-else />

  </div>
</template>

<script setup>
import AddTodoPage from './pages/AddTodoPage.vue';
import Header from './components/Header.vue';
import HomePage from './pages/HomePagePage.vue';
import ModifyTodoPage from './pages/ModifyTodoPage.vue';
import NotFoundPage from './pages/NotFoundPage.vue';


import { usePage } from './composable/usePage';

const { page, param } = usePage()


</script>