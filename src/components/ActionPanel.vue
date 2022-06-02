<script setup lang="ts">
import { Todo } from "../Todo";
import { ref } from "vue";
const name = ref('')
const emit = defineEmits<{
    (e: 'newTodo', todo: Todo): void
}>()
</script>

<template>
    <v-container>
        <v-row align="center">
            <v-text-field label="New Task" v-model="name" />
            <v-btn @click="emit('newTodo', { name })">
                Add
            </v-btn>
        </v-row>
    </v-container>
</template>