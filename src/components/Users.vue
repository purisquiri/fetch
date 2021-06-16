<template>
  <div v-for="user in users.data" :key="user.id">
    {{ user.first_name }} {{ user.last_name }}
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Users",

  async setup() {
    const users = ref(null);
    const userResponse = await fetch("https://reqres.in/api/users?delay=2");
    users.value = await userResponse.json();

    return { users };
  },
};
</script>

<style></style>
