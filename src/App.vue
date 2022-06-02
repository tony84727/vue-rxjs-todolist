<template>
  <v-app>
    <v-main>
      <ActionPanel @new-todo="newTodo" />
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
function newTodo(todo: Todo) {
  newTodo$.next(todo)
}
const todos = useObservable(newTodo$.pipe(scan((carry, c) => ([...carry, c]), [] as Todo[])))
</script>
