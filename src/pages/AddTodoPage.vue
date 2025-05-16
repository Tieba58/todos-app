<template>
    <h1>Nouvelle Tâche</h1>
    <div v-if="state === 'error'"> Imoossible d'enregistrer les données</div>
    <div v-else :aria-busy="state === 'loading'">
        <Grid>
            <PostCard v-for="post in posts" :key="post.id" :post="post" />
        </Grid>
    </div>
</template>

<script setup>
</script>