<script setup lang="ts">
import { ref } from "vue"
import { Icon } from "@iconify/vue"
import { RouterLink } from "vue-router"

const isSearchOpen = ref(false)
const isUserOpen = ref(false)
const isCartOpen = ref(false)
const isMenuOpen = ref(false)

const searchQuery = ref("")

const cartItems = ref([
    {
        id: 1,
        name: "Vintage Denim Jacket",
        size: "M",
        price: 39.99,
        image: "https://images.unsplash.com/photo-1551537482-f2075a1d41f2?w=300"
    },
    {
        id: 2,
        name: "Oversized Sweatshirt",
        size: "L",
        price: 29.99,
        image: "https://images.unsplash.com/photo-1556821840-3a63f95609a7?w=300"
    }
])

const categories = [
    "New Arrivals",
    "Clothing",
    "Dresses",
    "Tops",
    "Bottoms",
    "Jackets & Coats",
    "Knitwear",
    "Shoes",
    "Accessories",
]

const menuCategories = [
    "Men",
    "Women",
    "Vintage",
    "Y2K",
    "Streetwear",
    "Designer",
    "Luxury",
    "Sale",
]

const userModalState = ref<'signin' | 'signup' | 'recovery'>('signin')
const recoveryEmail = ref("")
const isCodeSent = ref(false)
const recoveryCode = ref("")
const newPassword = ref("")
const signUpEmail = ref("")
const signUpPassword = ref("")
const signUpName = ref("")

const closeAll = () => {
    isSearchOpen.value = false
    isUserOpen.value = false
    isCartOpen.value = false
    isMenuOpen.value = false
    userModalState.value = 'signin'
    isCodeSent.value = false
    recoveryEmail.value = ""
    recoveryCode.value = ""
    newPassword.value = ""
    signUpEmail.value = ""
    signUpPassword.value = ""
    signUpName.value = ""
}

const toggleSearch = () => {
    const state = !isSearchOpen.value
    closeAll()
    isSearchOpen.value = state
}

const toggleUser = () => {
    const state = !isUserOpen.value
    closeAll()
    isUserOpen.value = state
}

const toggleCart = () => {
    const state = !isCartOpen.value
    closeAll()
    isCartOpen.value = state
}

const toggleMenu = () => {
    const state = !isMenuOpen.value
    closeAll()
    isMenuOpen.value = state
}

const removeItem = (id: number) => {
    cartItems.value = cartItems.value.filter(item => item.id !== id)
}

const cartTotal = () => {
    return cartItems.value
        .reduce((total, item) => total + item.price, 0)
        .toFixed(2)
}

const handleSendCode = () => {
    if (recoveryEmail.value) {
        isCodeSent.value = true
        alert(`Verification code sent to ${recoveryEmail.value}!`)
    }
}

const handleResetPassword = () => {
    if (recoveryCode.value && newPassword.value) {
        alert("Password reset successfully!")
        closeAll()
    }
}
</script>

<template>
    <header class="navbar_wrapper">
        <div class="navbar_main">
            <button
                class="icon_button burger"
                @click="toggleMenu"
                aria-label="Open menu"
            >
                <Icon
                    :icon="
                        isMenuOpen
                            ? 'material-symbols:close'
                            : 'solar:hamburger-menu-linear'
                    "
                />
            </button>
            <div class="logo">
                <RouterLink to="/">
                    <img
                        src="https://thrifttale.com/cdn/shop/files/ThriftTale-logo-white.png?v=1689159400&width=280"
                        alt="ThriftTale"
                    />
                </RouterLink>
            </div>
            <div class="buttons">
                <button
                    class="icon_button"
                    @click="toggleUser"
                    aria-label="Account"
                >
                    <Icon icon="mingcute:user-1-line" />
                </button>
                <button
                    class="icon_button"
                    @click="toggleSearch"
                    aria-label="Search"
                >
                    <Icon icon="material-symbols:search" />
                </button>
                <button
                    class="icon_button cart_button"
                    @click="toggleCart"
                    aria-label="Shopping bag"
                >
                    <Icon icon="material-symbols:shopping-bag-outline-sharp" />
                    <span
                        v-if="cartItems.length"
                        class="cart_count"
                    >
                        {{ cartItems.length }}
                    </span>
                </button>
            </div>
        </div>
        <Transition name="search">
            <div
                v-if="isSearchOpen"
                class="search_container"
            >
                <div class="search_inner">
                    <Icon
                        class="search_icon"
                        icon="material-symbols:search"
                    />
                    <input
                        v-model="searchQuery"
                        type="text"
                        placeholder="Search for items..."
                        autofocus
                    />
                    <button
                        v-if="searchQuery"
                        class="clear_search"
                        @click="searchQuery = ''"
                    >
                        <Icon icon="material-symbols:close" />
                    </button>
                </div>
                <div
                    v-if="searchQuery"
                    class="search_results"
                >
                    <span>SEARCH RESULTS FOR</span>
                    <strong>"{{ searchQuery }}"</strong>
                </div>
                <div
                    v-else
                    class="popular_searches"
                >
                    <span>POPULAR SEARCHES</span>
                    <div class="search_tags">
                        <button>Vintage</button>
                        <button>Y2K</button>
                        <button>Denim</button>
                        <button>Oversized</button>
                    </div>
                </div>
            </div>
        </Transition>
        <Transition name="fade">
            <div
                v-if="isMenuOpen || isUserOpen || isCartOpen"
                class="overlay"
                @click="closeAll"
            ></div>
        </Transition>
        <Transition name="drawer-left">
            <aside
                v-if="isMenuOpen"
                class="side_menu left_menu"
            >
                <div class="drawer_header">
                    <span>MENU</span>
                    <button
                        class="close_button"
                        @click="closeAll"
                    >
                        <Icon icon="material-symbols:close" />
                    </button>
                </div>
                <nav class="drawer_nav">
                    <RouterLink
                        v-for="category in menuCategories"
                        :key="category"
                        to="#"
                        @click="closeAll"
                    >
                        <span>{{ category }}</span>

                        <Icon
                            icon="material-symbols:arrow-forward-ios"
                        />
                    </RouterLink>
                </nav>
                <div class="drawer_bottom">
                    <RouterLink to="#" @click="closeAll">
                        About Us
                    </RouterLink>

                    <RouterLink to="#" @click="closeAll">
                        Contact
                    </RouterLink>

                    <RouterLink to="#" @click="closeAll">
                        Shipping & Returns
                    </RouterLink>
                </div>

            </aside>
        </Transition>

        <Transition name="drawer-right">
            <aside
                v-if="isCartOpen"
                class="side_menu cart_menu"
            >
                <div class="drawer_header">
                    <span>YOUR BAG</span>
                    <button
                        class="close_button"
                        @click="closeAll"
                    >
                        <Icon icon="material-symbols:close" />
                    </button>
                </div>
                <div
                    v-if="!cartItems.length"
                    class="empty_cart"
                >
                    <Icon icon="material-symbols:shopping-bag-outline" />

                    <h3>Your bag is empty</h3>

                    <p>
                        Looks like you haven't added anything yet.
                    </p>

                    <RouterLink
                        to="#"
                        class="shop_button"
                        @click="closeAll"
                    >
                        SHOP NOW
                    </RouterLink>
                </div>

                <div
                    v-else
                    class="cart_content"
                >

                    <div class="cart_items">

                        <div
                            v-for="item in cartItems"
                            :key="item.id"
                            class="cart_item"
                        >

                            <img
                                :src="item.image"
                                :alt="item.name"
                            />

                            <div class="cart_item_info">

                                <div>
                                    <h4>{{ item.name }}</h4>

                                    <span>
                                        Size: {{ item.size }}
                                    </span>
                                </div>

                                <div class="cart_item_bottom">

                                    <strong>
                                        €{{ item.price.toFixed(2) }}
                                    </strong>

                                    <button
                                        @click="removeItem(item.id)"
                                    >
                                        Remove
                                    </button>

                                </div>

                            </div>

                        </div>

                    </div>

                    <div class="cart_footer">

                        <div class="subtotal">
                            <span>Subtotal</span>
                            <strong>€{{ cartTotal() }}</strong>
                        </div>

                        <p class="shipping_info">
                            Shipping calculated at checkout.
                        </p>

                        <button class="checkout_button">
                            CHECKOUT
                        </button>

                        <RouterLink
                            to="#"
                            class="view_cart"
                            @click="closeAll"
                        >
                            VIEW CART
                        </RouterLink>

                    </div>

                </div>

            </aside>
        </Transition>

        <Transition name="modal">
            <div
                v-if="isUserOpen"
                class="user_modal"
                @click.stop
            >

                <button
                    class="modal_close"
                    @click="closeAll"
                >
                    <Icon icon="material-symbols:close" />
                </button>

                <div
                    v-if="userModalState === 'signin'"
                    class="user_modal_content"
                >
                    <div class="modal_logo">
                        <Icon icon="mingcute:user-1-line" />
                    </div>
                    <span class="modal_small_title">WELCOME BACK</span>
                    <h2>Sign in to your account</h2>
                    <p>Access your orders, wishlist and saved items.</p>
                    <form @submit.prevent>
                        <label>Email</label>
                        <input type="email" placeholder="Your email" />
                        <label>Password</label>
                        <input type="password" placeholder="Your password" />
                        <div class="forgot_password">
                            <button
                                type="button"
                                class="link_button"
                                @click="userModalState = 'recovery'"
                            >
                                Forgot password?
                            </button>
                        </div>
                        <button class="login_button">SIGN IN</button>
                    </form>
                    <div class="register_text">
                        Don't have an account?
                        <button
                            type="button"
                            class="link_button link_button--bold"
                            @click="userModalState = 'signup'"
                        >
                            Create new account
                        </button>
                    </div>
                </div>

                <div
                    v-else-if="userModalState === 'signup'"
                    class="user_modal_content"
                >
                    <div class="modal_logo">
                        <Icon icon="mingcute:user-add-line" />
                    </div>
                    <span class="modal_small_title">JOIN US</span>
                    <h2>Create an account</h2>
                    <p>Start shopping and track your orders with ease.</p>
                    <form @submit.prevent>
                        <label>Full Name</label>
                        <input
                            v-model="signUpName"
                            type="text"
                            placeholder="Your full name"
                        />
                        <label>Email</label>
                        <input
                            v-model="signUpEmail"
                            type="email"
                            placeholder="Your email"
                        />
                        <label>Password</label>
                        <input
                            v-model="signUpPassword"
                            type="password"
                            placeholder="Create a password"
                        />
                        <button class="login_button" style="margin-top:20px">
                            CREATE ACCOUNT
                        </button>
                    </form>
                    <div class="register_text">
                        Already have an account?
                        <button
                            type="button"
                            class="link_button link_button--bold"
                            @click="userModalState = 'signin'"
                        >
                            Sign in
                        </button>
                    </div>
                </div>

                <div
                    v-else-if="userModalState === 'recovery'"
                    class="user_modal_content"
                >
                    <div class="modal_logo">
                        <Icon icon="material-symbols:lock-reset-outline" />
                    </div>

                    <template v-if="!isCodeSent">
                        <span class="modal_small_title">ACCOUNT RECOVERY</span>
                        <h2>Forgot your password?</h2>
                        <p>Enter your email and we'll send you a verification code.</p>
                        <form @submit.prevent="handleSendCode">
                            <label>Email</label>
                            <input
                                v-model="recoveryEmail"
                                type="email"
                                placeholder="Your email"
                                required
                            />
                            <button
                                class="login_button"
                                style="margin-top:20px"
                            >
                                SEND CODE
                            </button>
                        </form>
                    </template>

                    <template v-else>
                        <span class="modal_small_title">CHECK YOUR EMAIL</span>
                        <h2>Enter the code</h2>
                        <p>
                            We sent a code to
                            <strong>{{ recoveryEmail }}</strong>.
                            Use it to set a new password.
                        </p>
                        <form @submit.prevent="handleResetPassword">
                            <label>Verification Code</label>
                            <input
                                v-model="recoveryCode"
                                type="text"
                                placeholder="6-digit code"
                                required
                            />
                            <label>New Password</label>
                            <input
                                v-model="newPassword"
                                type="password"
                                placeholder="New password"
                                required
                            />
                            <button
                                class="login_button"
                                style="margin-top:20px"
                            >
                                RESET PASSWORD
                            </button>
                        </form>
                        <div class="register_text">
                            Didn't receive the code?
                            <button
                                type="button"
                                class="link_button link_button--bold"
                                @click="handleSendCode"
                            >
                                Resend
                            </button>
                        </div>
                    </template>

                    <div class="register_text" style="margin-top:14px">
                        <button
                            type="button"
                            class="link_button"
                            @click="userModalState = 'signin'"
                        >
                            ← Back to sign in
                        </button>
                    </div>
                </div>

            </div>
        </Transition>

    </header>
</template>

<style scoped>

* {
    box-sizing: border-box;
}

.navbar_wrapper {
    position: relative;
    z-index: 100;
}

.navbar_main {
    width: 100%;
    height: 64px;
    background-color: #fff;
    color: #000;
    padding: 10px 40px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    position: relative;
    z-index: 110;
}

.buttons {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 15px;
}

.icon_button {
    padding: 3px;
    margin: 0;
    background: transparent;
    border: none;
    border-radius: 50%;
    width: 34px;
    height: 34px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #000;
    cursor: pointer;
    transition:
        background-color 0.2s ease,
        transform 0.2s ease;
}

.icon_button:hover {
    background-color: rgba(0, 0, 0, 0.06);
}

.icon_button:active {
    transform: scale(0.92);
}

.icon_button svg {
    width: 25px;
    height: 25px;
}

.burger svg {
    width: 30px;
    height: 30px;
}

.logo {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

.logo a {
    display: flex;
    align-items: center;
    justify-content: center;
}

.logo img {
    width: 120px;
}

.cart_button {
    position: relative;
}

.cart_count {
    position: absolute;
    top: -2px;
    right: -2px;
    width: 16px;
    height: 16px;
    background: #000;
    color: #fff;
    border-radius: 50%;
    font-size: 9px;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
}

.search_container {
    position: absolute;
    top: 64px;
    left: 0;
    width: 100%;
    background: #fff;
    padding: 22px 40px 28px;
    border-top: 1px solid #eee;
    border-bottom: 1px solid #ddd;
    z-index: 105;
}

.search_inner {
    max-width: 900px;
    margin: 0 auto;
    height: 52px;
    border-bottom: 1px solid #111;
    display: flex;
    align-items: center;
    gap: 14px;
}

.search_icon {
    width: 24px;
    height: 24px;
    flex-shrink: 0;
}

.search_inner input {
    flex: 1;
    height: 100%;
    border: none;
    outline: none;
    font-family: inherit;
    font-size: 16px;
    background: transparent;
    color: #000;
}

.search_inner input::placeholder {
    color: #999;
}

.clear_search {
    border: none;
    background: transparent;
    cursor: pointer;
    display: flex;
    align-items: center;
    color: #000;
}

.clear_search svg {
    width: 20px;
    height: 20px;
}

.popular_searches,
.search_results {
    max-width: 900px;
    margin: 18px auto 0;
    display: flex;
    align-items: center;
    gap: 15px;
    font-size: 11px;
    letter-spacing: 1px;
}

.popular_searches > span,
.search_results > span {
    color: #888;
}

.search_tags {
    display: flex;
    gap: 7px;
}

.search_tags button {
    border: 1px solid #ddd;
    background: #fff;
    padding: 7px 12px;
    font-size: 11px;
    cursor: pointer;
    transition: 0.2s;
}

.search_tags button:hover {
    background: #000;
    color: #fff;
    border-color: #000;
}

.overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.35);
    z-index: 200;
    backdrop-filter: blur(2px);
}

.side_menu {
    position: fixed;
    top: 0;
    bottom: 0;
    width: 430px;
    background: #fff;
    z-index: 210;
    display: flex;
    flex-direction: column;
    box-shadow: 0 0 40px rgba(0, 0, 0, 0.12);
}

.left_menu {
    left: 0;
}

.cart_menu {
    right: 0;
}

.drawer_header {
    height: 76px;
    padding: 0 28px;
    border-bottom: 1px solid #e8e8e8;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 1.5px;
}

.close_button {
    width: 34px;
    height: 34px;
    border: none;
    background: transparent;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: 0.2s;
}

.close_button:hover {
    background: #f3f3f3;
}

.close_button svg {
    width: 22px;
    height: 22px;
}

.drawer_nav {
    padding: 15px 28px;
    overflow-y: auto;
}

.drawer_nav a {
    height: 55px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid #eee;
    color: #000;
    text-decoration: none;
    font-size: 15px;
    transition:
        padding 0.25s ease,
        color 0.2s ease;
}

.drawer_nav a:hover {
    padding-left: 8px;
}

.drawer_nav a svg {
    width: 15px;
    height: 15px;
    opacity: 0.45;
}

.drawer_bottom {
    margin-top: auto;
    border-top: 1px solid #eee;
    padding: 20px 28px;
    display: flex;
    flex-direction: column;
    gap: 13px;
}

.drawer_bottom a {
    color: #666;
    text-decoration: none;
    font-size: 12px;
    transition: color 0.2s;
}

.drawer_bottom a:hover {
    color: #000;
}

.cart_content {
    flex: 1;
    display: flex;
    flex-direction: column;
    min-height: 0;
}

.cart_items {
    flex: 1;
    overflow-y: auto;
    padding: 10px 28px;
}

.cart_item {
    display: flex;
    gap: 15px;
    padding: 18px 0;
    border-bottom: 1px solid #eee;
}

.cart_item img {
    width: 90px;
    height: 115px;
    object-fit: cover;
    background: #f5f5f5;
}

.cart_item_info {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-width: 0;
}

.cart_item_info h4 {
    margin: 0 0 7px;
    font-size: 13px;
    font-weight: 500;
    line-height: 1.4;
}

.cart_item_info span {
    color: #888;
    font-size: 11px;
}

.cart_item_bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.cart_item_bottom strong {
    font-size: 13px;
    font-weight: 500;
}

.cart_item_bottom button {
    border: none;
    background: transparent;
    padding: 0;
    color: #888;
    font-size: 10px;
    cursor: pointer;
    text-decoration: underline;
}

.cart_item_bottom button:hover {
    color: #000;
}

.cart_footer {
    border-top: 1px solid #ddd;
    padding: 22px 28px 25px;
    background: #fff;
}

.subtotal {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 14px;
}

.subtotal strong {
    font-weight: 500;
}

.shipping_info {
    margin: 9px 0 18px;
    color: #888;
    font-size: 10px;
}

.checkout_button {
    width: 100%;
    height: 48px;
    border: 1px solid #000;
    background: #000;
    color: #fff;
    font-size: 0.9rem;
    letter-spacing: 1.2px;
    cursor: pointer;
    transition: 0.2s;

}

.checkout_button:hover {
    background: #fff;
    color: #000;
}

.view_cart {
    display: block;
    text-align: center;
    margin-top: 14px;
    color: #000;
    font-size: 10px;
    letter-spacing: 1px;
    text-decoration: underline;
}

.empty_cart {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px;
    text-align: center;
}

.empty_cart > svg {
    width: 42px;
    height: 42px;
    margin-bottom: 20px;
}

.empty_cart h3 {
    margin: 0 0 8px;
    font-size: 17px;
    font-weight: 500;
}

.empty_cart p {
    margin: 0 0 25px;
    color: #888;
    font-size: 12px;
    line-height: 1.5;
}

.shop_button {
    background: #000;
    color: #fff;
    padding: 14px 28px;
    text-decoration: none;
    font-size: 10px;
    letter-spacing: 1.2px;
    transition: 0.2s;
}

.shop_button:hover {
    background: #222;
}

.user_modal {
    position: fixed;
    z-index: 220;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: min(440px, calc(100% - 30px));
    max-height: calc(100vh - 30px);
    overflow-y: auto;
    background: #fff;
    box-shadow: 0 20px 80px rgba(0, 0, 0, 0.2);
}

.modal_close {
    position: absolute;
    top: 18px;
    right: 18px;
    width: 34px;
    height: 34px;
    border: none;
    background: transparent;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2;
    transition: 0.2s;
}

.modal_close:hover {
    background: #f2f2f2;
}

.modal_close svg {
    width: 21px;
    height: 21px;
}

.user_modal_content {
    padding: 48px 45px 42px;
    text-align: center;
}

.modal_logo {
    width: 45px;
    height: 45px;
    margin: 0 auto 20px;
    border: 1px solid #ddd;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal_logo svg {
    width: 22px;
    height: 22px;
}

.modal_small_title {
    color: #888;
    font-size: 9px;
    letter-spacing: 1.7px;
}

.user_modal h2 {
    margin: 9px 0 10px;
    font-size: 22px;
    font-weight: 500;
}

.user_modal_content > p {
    margin: 0 auto 27px;
    max-width: 290px;
    color: #888;
    font-size: 12px;
    line-height: 1.5;
}

.user_modal form {
    text-align: left;
}

.user_modal label {
    display: block;
    margin: 16px 0 7px;
    font-size: 10px;
    letter-spacing: 0.5px;
}

.user_modal input {
    width: 100%;
    height: 44px;
    border: 1px solid #ddd;
    padding: 0 13px;
    outline: none;
    font-family: inherit;
    font-size: 12px;
    transition: border-color 0.2s;
}

.user_modal input:focus {
    border-color: #000;
}

.forgot_password {
    margin: 9px 0 20px;
    text-align: right;
}

.forgot_password a,
.forgot_password .link_button {
    color: #666;
    font-size: 10px;
}

.login_button {
    width: 100%;
    height: 46px;
    border: 1px solid #000;
    background: #000;
    color: #fff;
    cursor: pointer;
    font-size: 0.9rem;
    letter-spacing: 1.3px;
    transition: 0.2s;
}

.login_button:hover {
    background: #fff;
    color: #000;
}

.register_text {
    margin-top: 23px;

    color: #777;

    font-size: 11px;
}

.register_text a {
    color: #000;
    font-weight: 500;
}

.link_button {
    display: inline;
    border: none;
    background: transparent;
    padding: 0;
    margin: 0;
    font-family: inherit;
    font-size: inherit;
    color: #666;
    cursor: pointer;
    text-decoration: underline;
    transition: color 0.2s;
}

.link_button:hover {
    color: #000;
}

.link_button--bold {
    color: #000;
    font-weight: 500;
}

.search-enter-active,
.search-leave-active {
    transition:
        transform 0.3s ease,
        opacity 0.25s ease;
    transform-origin: top;
}

.search-enter-from,
.search-leave-to {
    opacity: 0;
    transform: translateY(-15px);
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}

.drawer-left-enter-active,
.drawer-left-leave-active {
    transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
}

.drawer-left-enter-from,
.drawer-left-leave-to {
    transform: translateX(-100%);
}

.drawer-right-enter-active,
.drawer-right-leave-active {
    transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
}

.drawer-right-enter-from,
.drawer-right-leave-to {
    transform: translateX(100%);
}

.modal-enter-active,
.modal-leave-active {
    transition:
        opacity 0.25s ease,
        transform 0.3s cubic-bezier(0.22, 1, 0.36, 1);
}
.modal-enter-from,
.modal-leave-to {
    opacity: 0;
    transform: translate(-50%, -46%) scale(0.97);
}

@media (max-width: 600px) {
    .navbar_main {
        height: 58px;
        padding: 8px 15px;
    }
    .logo img {
        width: 125px;
    }
    .buttons {
        gap: 3px;
    }
    .icon_button {
        width: 32px;
        height: 32px;
    }
    .search_container {
        top: 58px;
        padding: 18px 18px 22px;
    }
    .popular_searches,
    .search_results {
        align-items: flex-start;
        flex-direction: column;

        gap: 10px;
    }
    .side_menu {
        width: min(100%, 390px);
    }
    .user_modal_content {
        padding: 42px 25px 32px;
    }
    .cart_item img {
        width: 75px;
        height: 100px;
    }
}
</style>
