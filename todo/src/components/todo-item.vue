<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps<{ name: string }>()
    const emit = defineEmits(['delete'])
    let complete = ref(false)

    const changeStatus = (e) => {
        complete.value = !complete.value
    }

    const killItem = () => {
        emit('delete', props.name)
    }
</script>

<template>
    <li :class="{ done: complete}">
        {{ props.name }}
        <button @click="changeStatus">Toggle</button>
        <button @click="killItem">X</button>
    </li>
</template>

<style scoped>
    .done{
        text-decoration-line: line-through;
    }

    button {
        margin: .10rem
    }
</style>