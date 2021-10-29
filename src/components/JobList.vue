<script lang="ts">
import { defineComponent, PropType } from "vue";

// types
import { Job } from "../types/Jobs";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
  },
});
</script>

<template>
  <div class="job-list">
    <ul>
      <li v-for="job in jobs" :key="job.id">{{}}</li>
    </ul>
  </div>
</template>

<style scoped></style>
