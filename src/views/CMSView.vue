<script setup lang="ts">
    import CMSNavbar from "../components/CMS/navbar.vue";
    import CMSSidebar from "../components/CMS/sidebar.vue"
</script>
<template>
    <div class="cms_main">
        <CMSNavbar/>
        <div class="content_wrapper">
            <CMSSidebar/>
        </div>
    </div>
</template>
<style lang="css" scoped>
    .cms_main {
        width: 100%;
        height: 100vh;
        display: flex;
        flex-direction: column;
        overflow-y: hidden;
    }
    .content_wrapper {
        display: flex;
        flex-direction: row;
        width: 100%;
    }
</style>