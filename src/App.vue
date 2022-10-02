<script setup lang="ts">
import TheHeader from "@/components/TheHeader.vue";
import EntryEditor from "./components/EntryEditor.vue";
import EntryCard from "@/components/EntryCard.vue";
import { provide, reactive, inject } from "vue";
import { userInjectionKey } from "./injectionKeys";
import type User from "./types/User";
import type Entry from "./types/Entry";

const entries: Entry[] = reactive([]);
const user: User = reactive({
  id: 1,
  username: "mdashikurrahman_io",
  settings: [],
});
provide(userInjectionKey, user);

// in child component
const injectUser = inject(userInjectionKey);

console.log(user.id);
const handleCreateEntry = (entry: Entry) =>{
  entries.unshift(entry);
}
</script>

<template>
  <main class="container m-auto p-10">
    <TheHeader />
    <EntryEditor @@create="handleCreateEntry"/>
    <ul>
      <li v-for="entry in entries" :key="entry.id">
        <EntryCard />
      </li>
    </ul>
  </main>
</template>
