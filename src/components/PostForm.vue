<template>
    <form action="" @submit.prevent="onSubmit">
        <Alert type="danger" v-if="state === 'error'" @close="state = 'idle'">
            Mise à jour échouée
        </Alert>
        <Field label="Titre" id="title" v-model="todo.title" />
        <Field label="Contenu" id="content" v-model="todo.body" type="textarea" />
        <Field label="Date" id="date" v-model="post.date" type="date" />
        <button :disabled="state === 'loading'">Modifier</button>
    </form>

</template>

<script setup>
import { ref } from 'vue';
import Field from './Field.vue';
import Alert from './Alert.vue';


const emits = defineEmits('save')

const props = defineProps({
    todo: Object
})

const state = ref('idle')

const onSubmit = () => {
    state.value = 'loading'


}
</script>