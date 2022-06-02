<script setup lang="ts">
import { Todo } from "../Todo";
import { ref } from "vue";
const name = ref('')
defineProps<{ newTodo: Todo | undefined }>()
</script>

<template>
    <v-container>
        <v-row align="center">
            <v-text-field label="New Task" v-model="name" />
            <v-btn @click="newTodo = { name }">
                Add
            </v-btn>
        </v-row>
    </v-container>
</template>