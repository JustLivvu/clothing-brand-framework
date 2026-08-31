<script setup lang="ts">
import { Icon } from "@iconify/vue"
</script>

<template>
    <aside class="sidebar_main">
        <div class="sidebar_section">
            <div class="sidebar_category">STORE</div>

            <button class="sidebar_item active">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:checkroom-outline" />
                </span>
                <span class="sidebar_label">Products</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:collections-bookmark-outline" />
                </span>
                <span class="sidebar_label">Collections</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:category-outline" />
                </span>
                <span class="sidebar_label">Categories</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:inventory-2-outline" />
                </span>
                <span class="sidebar_label">Inventory</span>
            </button>
        </div>

        <div class="sidebar_section">
            <div class="sidebar_category">SALES</div>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:receipt-long-outline" />
                </span>
                <span class="sidebar_label">Orders</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:group-outline" />
                </span>
                <span class="sidebar_label">Customers</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:local-offer-outline" />
                </span>
                <span class="sidebar_label">Discounts</span>
            </button>
        </div>

        <div class="sidebar_section">
            <div class="sidebar_category">ANALYTICS</div>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:dashboard-outline" />
                </span>
                <span class="sidebar_label">Overview</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:bar-chart-4-bars" />
                </span>
                <span class="sidebar_label">Sales</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:trending-up" />
                </span>
                <span class="sidebar_label">Best Sellers</span>
            </button>
        </div>

        <div class="sidebar_section">
            <div class="sidebar_category">CONTENT</div>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:description-outline" />
                </span>
                <span class="sidebar_label">Pages</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:image-outline" />
                </span>
                <span class="sidebar_label">Media</span>
            </button>

            <button class="sidebar_item">
                <span class="icon_wrapper">
                    <Icon icon="material-symbols:menu" />
                </span>
                <span class="sidebar_label">Navigation</span>
            </button>
        </div>
    </aside>
</template>

<style scoped>
.sidebar_main {
    width: 240px;
    min-height: 100vh;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    gap: 28px;
    padding: 24px 14px;
    background: #fafafa;
    border-right: 1px solid #eaeaea;
    font-family: "Inter", sans-serif;
    overflow-y: scroll;
}

.sidebar_section {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.sidebar_category {
    padding: 0 12px;
    margin-bottom: 8px;
    font-size: 0.68rem;
    font-weight: 600;
    letter-spacing: 0.06em;
    color: #9a9a9a;
}

.sidebar_item {
    position: relative;
    width: 100%;
    min-height: 42px;
    display: flex;
    align-items: center;
    gap: 11px;
    padding: 8px 12px;
    border: none;
    border-radius: 9px;
    outline: none;
    background: transparent;
    color: #5f6368;
    font-family: inherit;
    font-size: 0.88rem;
    font-weight: 500;
    text-align: left;
    cursor: pointer;
    transition:
        background-color 0.18s ease,
        color 0.18s ease,
        transform 0.18s ease;
}

.sidebar_item:hover {
    background: #f0f0f0;
    color: #222;
}

.sidebar_item:active {
    transform: scale(0.98);
}

.sidebar_item.active {
    background: #111;
    color: white;
}

.sidebar_item.active:hover {
    background: #1c1c1c;
}

.icon_wrapper {
    width: 30px;
    height: 30px;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 7px;
    background: #eeeeee;
    color: #555;

    transition:
        background-color 0.18s ease,
        color 0.18s ease;
}

.icon_wrapper svg {
    width: 18px;
    height: 18px;
}

.sidebar_item.active .icon_wrapper {
    background: rgba(255, 255, 255, 0.14);
    color: white;
}

.sidebar_label {
    white-space: nowrap;
}
</style>