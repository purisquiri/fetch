<template>
  <div v-if="error">{{ error }}</div>
  <div v-else v-for="user in users.data" :key="user.id">
    {{ user.first_name }} {{ user.last_name }}
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Users",

  async setup() {
    const error = ref(null);
    const users = ref(null);

    try {
      const userResponse = await fetch("https://reqres.in/api/users?delay=2");
      users.value = await userResponse.json();
    } catch (e) {
      error.value = e;
    }

    return { users, error };
  },
};
</script>
