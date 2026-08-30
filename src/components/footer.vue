<script setup lang="ts">
import { Icon } from "@iconify/vue"
import { RouterLink } from "vue-router"

const year = new Date().getFullYear()

const links = [
    {
        heading: "Shop",
        items: ["New Arrivals", "Men", "Women", "Vintage", "Y2K", "Streetwear", "Sale"]
    },
    {
        heading: "Help",
        items: ["FAQ", "Shipping & Returns", "Size Guide", "Track Order", "Contact Us"]
    },
    {
        heading: "Company",
        items: ["About Us", "Sustainability", "Careers", "Press", "Affiliate Program"]
    }
]

const socials = [
    { icon: "mdi:instagram", label: "Instagram" },
    { icon: "ic:baseline-tiktok", label: "TikTok" },
    { icon: "mdi:pinterest", label: "Pinterest" },
    { icon: "mdi:twitter", label: "Twitter" }
]
</script>

<template>
    <footer class="footer">
        <div class="footer_top">
            <div class="footer_brand">
                <RouterLink to="/" class="footer_logo">
                    <img
                        src="https://thrifttale.com/cdn/shop/files/ThriftTale-logo-white.png?v=1689159400&width=280"
                        alt="ThriftTale"
                    />
                </RouterLink>
                <p class="footer_tagline">
                    Curated secondhand fashion.<br />Wear it again. Wear it better.
                </p>
                <div class="footer_socials">
                    <a
                        v-for="social in socials"
                        :key="social.label"
                        href="#"
                        :aria-label="social.label"
                        class="social_link"
                    >
                        <Icon :icon="social.icon" />
                    </a>
                </div>
            </div>
            <nav class="footer_links">
                <div
                    v-for="col in links"
                    :key="col.heading"
                    class="footer_col"
                >
                    <span class="footer_col_heading">{{ col.heading }}</span>
                    <ul>
                        <li v-for="item in col.items" :key="item">
                            <RouterLink to="#">{{ item }}</RouterLink>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>
        <div class="footer_newsletter">
            <span class="footer_col_heading">Stay in the loop</span>
            <p>New drops, exclusive deals and style inspo - straight to your inbox.</p>
            <form class="newsletter_form" @submit.prevent>
                <input type="email" placeholder="Your email address" />
                <button type="submit">SUBSCRIBE</button>
            </form>
        </div>
        <div class="footer_bottom">
            <span>© {{ year }} ThriftTale. All rights reserved.</span>
            <div class="footer_legal">
                <RouterLink to="#">Privacy Policy</RouterLink>
                <RouterLink to="#">Terms of Service</RouterLink>
                <RouterLink to="#">Cookie Settings</RouterLink>
            </div>
        </div>
    </footer>
</template>

<style scoped>
* {
    box-sizing: border-box;
}

.footer {
    margin-top: 60px;
    background: #111;
    color: #fff;
    padding: 60px 40px 28px;
    font-family: inherit;
}

.footer_top {
    display: flex;
    gap: 60px;
    padding-bottom: 48px;
    border-bottom: 1px solid #2a2a2a;
}

.footer_brand {
    flex-shrink: 0;
    max-width: 240px;
}

.footer_logo img {
    width: 110px;
    margin-bottom: 18px;
    display: block;
}

.footer_tagline {
    color: #999;
    font-size: 12px;
    line-height: 1.7;
    margin: 0 0 24px;
}

.footer_socials {
    display: flex;
    gap: 12px;
}

.social_link {
    width: 34px;
    height: 34px;
    border: 1px solid #2a2a2a;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #aaa;
    text-decoration: none;
    transition: 0.2s;
}

.social_link:hover {
    border-color: #fff;
    color: #fff;
}

.social_link svg {
    width: 17px;
    height: 17px;
}

.footer_links {
    flex: 1;
    display: flex;
    gap: 40px;
    justify-content: flex-end;
}

.footer_col {
    display: flex;
    flex-direction: column;
    gap: 14px;
    min-width: 120px;
}

.footer_col_heading {
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 1.8px;
    text-transform: uppercase;
    color: #fff;
}

.footer_col ul {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.footer_col a {
    color: #888;
    text-decoration: none;
    font-size: 12px;
    transition: color 0.2s;
}

.footer_col a:hover {
    color: #fff;
}

.footer_newsletter {
    padding: 40px 0;
    border-bottom: 1px solid #2a2a2a;
    max-width: 480px;
}

.footer_newsletter p {
    color: #888;
    font-size: 12px;
    line-height: 1.6;
    margin: 10px 0 18px;
}

.newsletter_form {
    display: flex;
    height: 44px;
    gap: 0;
}

.newsletter_form input {
    flex: 1;
    background: #1a1a1a;
    border: 1px solid #2a2a2a;
    border-right: none;
    color: #fff;
    padding: 0 14px;
    font-family: inherit;
    font-size: 12px;
    outline: none;
    transition: border-color 0.2s;
}

.newsletter_form input::placeholder {
    color: #555;
}

.newsletter_form input:focus {
    border-color: #555;
}

.newsletter_form button {
    background: #fff;
    color: #000;
    border: none;
    padding: 0 20px;
    font-family: inherit;
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 1.3px;
    cursor: pointer;
    transition: 0.2s;
    white-space: nowrap;
}

.newsletter_form button:hover {
    background: #ddd;
}

.footer_bottom {
    padding-top: 28px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 10px;
    color: #555;
}

.footer_legal {
    display: flex;
    gap: 22px;
}

.footer_legal a {
    color: #555;
    text-decoration: none;
    transition: color 0.2s;
}

.footer_legal a:hover {
    color: #aaa;
}

@media (max-width: 768px) {
    .footer {
        padding: 48px 20px 24px;
    }

    .footer_top {
        flex-direction: column;
        gap: 36px;
    }

    .footer_brand {
        max-width: 100%;
    }

    .footer_links {
        justify-content: flex-start;
        flex-wrap: wrap;
        gap: 28px;
    }

    .footer_bottom {
        flex-direction: column;
        align-items: flex-start;
        gap: 14px;
    }

    .footer_legal {
        flex-wrap: wrap;
        gap: 14px;
    }
}
</style>
