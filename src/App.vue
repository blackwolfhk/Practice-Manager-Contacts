<template>
  <!-- <Spinner /> -->
  <NavBar />
  <router-view />
</template>

<script>
import NavBar from "@/components/NavBar";
// import Spinner from "@/components/Spinner";

export default {
  name: "App",
  components: {
    // Spinner,
    NavBar,
  },
};
</script>

<style></style>
