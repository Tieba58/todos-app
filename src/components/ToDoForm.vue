<template>
    <form @submit.prevent="handleSubmit">
        <Alert type="danger" v-if="state === 'error'" @close="state = 'idle'">
            Mise à jour échouée
        </Alert>

        <Field id="title" label="Titre" v-model="localTodo.title" />
        <Field id="content" label="Contenu" type="textarea" v-model="localTodo.body" />
        <Field id="date" label="Date" type="date" v-model="localTodo.date" />

        <button type="submit">{{ type }}</button>
    </form>
</template>

<script setup>
import { ref, reactive, watch } from 'vue'
import Field from './Field.vue'
import Alert from './Alert.vue'

// Props
const props = defineProps({
    type: String,
    todo: Object,
    onSave: Function, // Fonction passée par le parent (création ou mise à jour)
})

// État du formulaire
const state = ref('idle')

// Cloner les données dans un `reactive` local pour éviter modification directe
const localTodo = reactive({
    title: '',
    body: '',
    date: '',
    completed: false,
})

// Sync initiale
watch(
    () => props.todo,
    (newVal) => {
        Object.assign(localTodo, newVal)
    },
    { immediate: true }
)

const handleSubmit = () => {
    try {
        state.value = 'loading'
        props.onSave({ ...localTodo }) // On envoie les données au parent
        state.value = 'idle'
    } catch (e) {
        state.value = 'error'
    }
}
</script>