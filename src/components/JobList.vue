<script lang="ts">
import { OrderTerm } from "@/types/OrderTerm";
import { computed, defineComponent, PropType } from "vue";

// types
import { Job } from "../types/Jobs";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return { orderedJobs };
  },
});
</script>

<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="../assets/icons/rupee.svg" alt="rupee-icon" />
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Optio odit
            temporibus cumque blanditiis eveniet quidem corrupti ratione
            expedita rem, nihil a fuga deserunt ad eos eum quia odio nostrum,
            nemo quam voluptate? Accusantium iure labore hic ullam esse quam aut
            explicabo quos at, corporis quisquam maiores distinctio perferendis,
            voluptatibus animi repellendus reiciendis enim, rem officia soluta
            fugit ducimus? Provident nostrum quibusdam in totam hic esse,
            facilis quis earum a mollitia minima. Fuga libero earum veritatis
            cum. Velit iusto incidunt quas voluptatibus quam quo beatae impedit
            ipsa quibusdam iure sed, eos accusantium quasi nostrum officiis,
            fuga deserunt aliquid quisquam distinctio voluptas.
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
.list-move {
  transition: all 1s;
}
</style>
