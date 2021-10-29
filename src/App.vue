<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "App",
  setup() {
    // name
    const name = ref<string>("Link");
    const changeName = (newName: string): void => {
      name.value = newName;
    };

    // age
    const age = ref<number | string>(25);
    const changeAge = (newAge: number | string): void => {
      age.value = newAge;
    };

    return { name, changeName, age, changeAge };
  },
});
</script>

<template>
  <div class="app">
    <p>
      {{ name }}
      -
      {{ age }}
    </p>
    <button @click="changeName('Zelda')">Change Name</button>
    <button @click="changeAge(30)">Change Name</button>
  </div>
</template>

<style></style>
