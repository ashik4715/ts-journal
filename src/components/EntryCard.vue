<script lang="ts" setup>
import DateDisplay from "./DateDisplay.vue";
import UseEmojis from "@/composables/UseEmojis";
import type Entry from "@/types/Entry";
import { userInjectionKey } from "@/injectionKeys";
import { inject } from "vue";

const user = inject(userInjectionKey);
const { findEmoji } = UseEmojis();
// defineProps<{
//   entry: Entry;
// }>();
</script>
<template>
  <div class="entry-card">
    <div class="entry-card-body">
      <component width="75" :is="findEmoji('Happy')"></component>
      <div class="entry-text">Today I enjoyed walking the dog in the park.</div>
    </div>
    <div class="entry-footer">
      <DateDisplay :date="new Date()" class="mr-2" />
      |
      <span class="ml-2">{{ user?.username || "anonymous" }}</span>
    </div>
  </div>
</template>
