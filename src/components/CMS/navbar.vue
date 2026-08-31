<script setup lang="ts">
</script>
<template>
    <div class="navbar_main">
        <span>Welcome back, admin</span>
        <button class="sign_out_btn">Sign Out</button>
    </div>
</template>
<style lang="css" scoped>
    .navbar_main {
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        box-sizing: border-box;
        padding: 15px;
    }
    .sign_out_btn {
        padding: 10px;
        background-color: black;
        color: white;
        font-family: "Inter", sans-serif;
        border: none;
        outline: none;
        cursor: pointer;
        border: 1px solid black;
        transition: 0.2s;
    }
    .sign_out_btn:hover {
        color: black;
        background-color: white;
    }
</style>