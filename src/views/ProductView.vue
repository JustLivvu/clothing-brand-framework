<script setup lang="ts">
    import { Icon } from "@iconify/vue";
    import Announcement from "../components/announcement.vue";
    import Navbar from "../components/navbar.vue";
</script>
<template>
    <div class="product_main">
        <Announcement/>
        <Navbar/>
        <div class="product_info">
            <div class="product_photos">
                <div class="product_image">

                </div>
                <div class="product_images_wrapper">
                    <div class="product_change_pic"></div>
                    <div class="product_change_pic"></div>
                    <div class="product_change_pic"></div>
                    <div class="product_change_pic"></div>
                </div>
            </div>
            <div class="product_details">
                <span class="product_title">GRAPHIC T-SHIRT</span>
                <span class="product_description">The example product description</span>
                <span class="product_price">29,99 €</span>
                <div class="size_guide_text">
                    <Icon icon="griddy-icons:ruler"/>
                    <span>Size guide</span>
                </div>
                <div class="product_sizes">
                    <div class="size_box">XXXS</div>
                    <div class="size_box">XXS</div>
                    <div class="size_box">XS</div>
                    <div class="size_box">S</div>
                    <div class="size_box">M</div>
                    <div class="size_box">L</div>
                    <div class="size_box">XL</div>
                    <div class="size_box">XXL</div>
                </div>
                <span class="out_of_stock">Out of stock? <button class="notify">Get notified</button></span>
                <button class="add_to_bag_btn">ADD TO BAG</button>
                <div class="long_desc">
                    <span>
T-shirt with crewneck is crafted from fluid cotton jersey, featuring a seasonal logo print on the chest. Cut to a regular fit and hip length.
Product details
<br><br>
Product information
<br>
    Shell: 50% Cotton,<br> 50% Viscose


                    </span>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="css" scoped>
    .long_desc {
        margin-top: 30px;
        font-size: 0.8rem;
    }
    .add_to_bag_btn {
        font-family: "Inter", sans-serif;
        width: 100%;
        height: 60px;
        border: 1px solid #000;
        background: #000;
        color: #fff;
        cursor: pointer;
        font-size: 0.9rem;
        letter-spacing: 1.3px;
        transition: 0.2s;
    }
    .add_to_bag_btn:hover {
        background-color: white;
        color: black;
    }
    .out_of_stock {
        margin-top: 20px;
        margin-bottom: 20px;
        font-size: 0.8rem;
    }
    .notify {
        border: none;
        background-color: transparent;
        padding: 0;
        font-family: "Inter", sans-serif;
        color: #0018a8;
        text-decoration: underline;
        font-size: 0.8rem;
    }
    .size_guide_text {
        font-size: 0.8rem;
        display: flex;
        flex-direction: row;
        color: #0018a8;
        gap: 3px;
        margin-bottom: 3px;
        justify-content: end;
        margin-right: 8px;
    }
    .product_price {
        font-size: 2rem;
        margin-top: 10px;
        font-weight: 300;
        margin-bottom: 30px;
    }
    .product_sizes {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        gap: 0px;
    }
    .size_box {
        width: 100px;
        box-sizing: border-box;
        height: 50px;
        padding: 5px;
        border: 1px solid rgb(207, 207, 207);
        font-size: 0.8rem;
        margin-right: -1px;
        margin-bottom: -1px;
    }

    .product_details {
        display: flex;
        flex-direction: column;
        width: 500px;
    }
    .product_description {
        color: rgb(136, 136, 136);
        font-size: 0.9rem;
    }
    .product_title {
        font-weight: 300;
        font-size: 0.9rem;
    }
    .product_main {
        width: 100%;
        height: 100vh;
        display: flex;
        flex-direction: column;
    }
    .product_info {
        width: 100%;
        padding: 50px 70px;
        box-sizing: border-box;
        display: flex;
        flex-direction: row;
        gap: 80px;
    }
    .product_photos {
        display: flex;
        flex-direction: row;
        gap: 10px;
    }
    .product_images_wrapper {
        display: flex;
        gap: 10px;
        flex-direction: column;
    }
    .product_change_pic {
        background-color: rgb(207, 207, 207);
        width: 82px;
        height: 82px;
        cursor: pointer;
    }
    .product_image {
        width: 600px;
        height: 600px;
        background-color: rgb(207, 207, 207);
    }
</style>