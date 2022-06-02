<template>
  <v-app>
    <v-main>
      <!-- works -->
      <ActionPanel @new-todo="(todo) => newTodo$.next(todo)" />
      <!-- doesn't work -->
      <ActionPanel @new-todo="newTodo$.next.bind(newTodo$)" />
      <List :todos="todos ?? []" />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import ActionPanel from './components/ActionPanel.vue'
import List from "./components/List.vue"
import { useObservable } from "@vueuse/rxjs"
import { scan, Subject } from 'rxjs';
import { Todo } from './Todo';
const newTodo$ = new Subject<Todo>();
const todos = useObservable(newTodo$.pipe(scan((carry, c) => ([...carry, c]), [] as Todo[])))
</script>
