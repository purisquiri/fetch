<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div v-if="error">Parent: {{ error }}</div>
    <Suspense>
      <template #default>
        <Users />
      </template>
      <template #fallback>
        <div>Loading users...</div>
      </template>
    </Suspense>
  </div>
</template>

<script>
import Users from "./components/Users.vue";
import { ref, onErrorCaptured } from "vue";

export default {
  name: "App",
  setup() {
    const error = ref(null);

    onErrorCaptured((e) => {
      error.value = e;
    });

    return { error };
  },
  components: {
    Users,
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>
