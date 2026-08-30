<script setup lang="ts">
import Announcement from "../components/announcement.vue";
import Navbar from "../components/navbar.vue";
import Footer from "../components/footer.vue";
</script>

<template>
  <div class="home_main">
    <Announcement/>
    <Navbar/>
    <Footer/>
  </div>
</template>
<style lang="css" scoped>
  .home_main {
    display: flex;
    flex-direction: column;
    width: 100%;
    min-height: 100vh;
  }
</style>