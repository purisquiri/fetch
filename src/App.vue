<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Suspense>
    <Users />
  </Suspense>
</template>

<script>
import Users from "./components/Users.vue";

export default {
  name: "App",
  components: {
    Users,
  },
};
</script>

<style></style>
