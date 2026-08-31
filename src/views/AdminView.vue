<script setup lang="ts">
    import { Icon } from "@iconify/vue"
</script>
<template>
    <div class="admin_main">
        <div class="admin_login_box">
            <span>Access admin panel</span>
            <input type="text" placeholder="Enter your e-mail"/>
            <input type="password" placeholder="Enter your password"/>
            <input type="password" placeholder="Enter your security code" maxlength="5"/>
            <button><Icon icon="mdi:lock"/>Authenticate</button>
        </div>
    </div>
</template>
<style lang="css" scoped>
    .admin_main {
        width: 100%;
        height: 100vh;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
    }
    .admin_login_box {
        width: 300px;
        padding: 10px;
        height: auto;
        border: 1px solid gray;
        display: flex;
        flex-direction: column;
        gap: 10px;
        justify-content: center;
    }
    .admin_login_box span {
        font-size: 0.8rem;
        width: fit-content;
    }
    .admin_login_box input {
        width: 100%;
        padding: 5px;
        border: none;
        outline: none;
    }
    .admin_login_box button {
        border: none;
        outline: none;
        padding: 10px;
        width: 100%;
        color: white;
        background-color: black;
        cursor: pointer;
        font-family: "Inter", sans-serif;
        display: flex;
        flex-direction: row;
        gap: 5px;
        align-items: center;
        justify-content: center;
        transition: 0.2s;
        border: 1px solid black;
    }
    .admin_login_box button:hover {
        background-color: white;
        color: black;
    }
</style>