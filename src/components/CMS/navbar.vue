<script setup lang="ts">
import { Icon } from "@iconify/vue"
</script>

<template>
    <header class="navbar_main">
        <div class="navbar_left">
            <span class="navbar_title">Welcome back, admin</span>
            <span class="navbar_subtitle">Here's what's happening today.</span>
        </div>
        <div class="navbar_right">
            <button class="icon_btn" title="Notifications">
                <Icon icon="material-symbols:bell" />
            </button>
            <div class="navbar_divider"></div>
            <div class="profile">
                <div class="avatar">
                    A
                </div>
                <div class="profile_info">
                    <span class="profile_name">Admin</span>
                    <span class="profile_role">Administrator</span>
                </div>
                <button class="sign_out_btn">
                    <Icon icon="material-symbols:logout-rounded" />
                    <span>Sign out</span>
                </button>
            </div>
        </div>
    </header>
</template>

<style scoped>
.navbar_main {
    width: 100%;
    height: 72px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-sizing: border-box;
    padding: 10px 24px;
    background: #ffffff;
    border-bottom: 1px solid #eaeaea;
    font-family: "Inter", sans-serif;
}

.navbar_left {
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.navbar_title {
    font-size: 0.95rem;
    font-weight: 600;
    color: #202020;
}

.navbar_subtitle {
    font-size: 0.78rem;
    color: #999;
}

/* RIGHT */

.navbar_right {
    display: flex;
    align-items: center;
    gap: 14px;
}

.icon_btn {
    width: 36px;
    height: 36px;

    display: flex;
    align-items: center;
    justify-content: center;

    padding: 0;

    border: 1px solid #e5e5e5;
    border-radius: 8px;

    background: #fff;
    color: #555;

    cursor: pointer;

    transition:
        background-color 0.18s ease,
        border-color 0.18s ease,
        color 0.18s ease;
}

.icon_btn:hover {
    background: #f5f5f5;
    border-color: #d8d8d8;
    color: #111;
}

.icon_btn svg {
    width: 19px;
    height: 19px;
}

.navbar_divider {
    width: 1px;
    height: 30px;
    background: #e8e8e8;
}

/* PROFILE */

.profile {
    display: flex;
    align-items: center;
    gap: 10px;
}

.avatar {
    width: 34px;
    height: 34px;

    display: flex;
    align-items: center;
    justify-content: center;

    border-radius: 9px;

    background: #111;
    color: #fff;

    font-size: 0.8rem;
    font-weight: 600;
}

.profile_info {
    display: flex;
    flex-direction: column;
    gap: 2px;
    margin-right: 6px;
}

.profile_name {
    font-size: 0.82rem;
    font-weight: 600;
    color: #222;
}

.profile_role {
    font-size: 0.7rem;
    color: #999;
}

/* SIGN OUT */

.sign_out_btn {
    height: 36px;

    display: flex;
    align-items: center;
    gap: 7px;

    padding: 0 12px;

    border: 1px solid #e2e2e2;
    border-radius: 8px;
    outline: none;

    background: #fff;
    color: #555;

    font-family: "Inter", sans-serif;
    font-size: 0.78rem;
    font-weight: 500;

    cursor: pointer;

    transition:
        background-color 0.18s ease,
        border-color 0.18s ease,
        color 0.18s ease;
}

.sign_out_btn:hover {
    background: #f5f5f5;
    border-color: #d5d5d5;
    color: #111;
}

.sign_out_btn svg {
    width: 17px;
    height: 17px;
}
</style>
