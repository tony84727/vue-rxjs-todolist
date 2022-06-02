<template>
    <ol>
        <li v-for="todo in todos">
            {{ todo.name }}
        </li>
    </ol>
</template>
<script setup lang="ts">import { Todo } from '../Todo';
defineProps<{todos: Todo[]}>()
</script>