<script setup lang="ts">
import Announcement from "../components/announcement.vue";
import Navbar from "../components/navbar.vue";
</script>

<template>
  <div class="home_main">
    <Announcement/>
    <Navbar/>
  </div>
</template>
<style lang="css" scoped>
  .home_main {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100vh;
  }
</style>