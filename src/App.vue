<template>
  <Header />
  <main>
    <RouterView />
  </main>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import Header from "./components/Header.vue";

export default {
  components: {
    Header
  }
}
</script>

<style scoped>

</style>
