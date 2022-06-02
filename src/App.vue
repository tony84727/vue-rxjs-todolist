<template>
  <v-app>
    <v-main>
      <ActionPanel :new-todo="newTodoRef" />
      <v-btn @click="newTodoRef = { name: 'From Ref' }">
        Ref
      </v-btn>
      <List :todos="todos ?? []" />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import ActionPanel from './components/ActionPanel.vue'
import List from "./components/List.vue"
import { useObservable, useSubject } from "@vueuse/rxjs"
import { scan, Subject } from 'rxjs';
import { Todo } from './Todo';
const newTodo$ = new Subject<Todo>();
const newTodoRef = useSubject(newTodo$);
const todos = useObservable(newTodo$.pipe(scan((carry, c) => ([...carry, c]), [] as Todo[])))
</script>
