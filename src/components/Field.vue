<template>
    <label :for="id">{{ label }}</label>
    <div v-if="type === 'textarea'">
        <textarea :id="id" v-model="model">
        </textarea>
    </div>
    <div v-else>
        <input :type="type" :id="id" v-model="model"/>
    </div>

</template>

<script setup>

const props = defineProps({
    label: String,
    id: String,
    type: {
        type: String,
        default: 'text'
    },
})

const model = defineModel()
</script>