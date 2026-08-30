<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { Icon } from "@iconify/vue";

const announcements = [
    "THIS IS TEST ANNOUNCEMENT, THE CONTENT CAN BE CHANGED IN CMS PANEL",
    "SECOND TEST ANNOUNCEMENT, THE CONTENT CAN BE CHANGED IN CSM PANEL",
];

const currentAnnouncement = ref(0);

let interval: ReturnType<typeof setInterval>;

const nextAnnouncement = () => {
    currentAnnouncement.value =
        (currentAnnouncement.value + 1) % announcements.length;

    resetInterval();
};

const previousAnnouncement = () => {
    currentAnnouncement.value =
        (currentAnnouncement.value - 1 + announcements.length) %
        announcements.length;

    resetInterval();
};

const resetInterval = () => {
    clearInterval(interval);

    interval = setInterval(() => {
        currentAnnouncement.value =
            (currentAnnouncement.value + 1) % announcements.length;
    }, 4000);
};

onMounted(() => {
    resetInterval();
});

onUnmounted(() => {
    clearInterval(interval);
});
</script>

<template>
    <div class="annoucement_main">
        <Transition name="announcement-fade" mode="out-in">
            <div
                class="announcement_content"
                :key="currentAnnouncement"
            >
                <button
                    class="announcement_change_btn"
                    @click="previousAnnouncement"
                    aria-label="Previous announcement"
                >
                    <Icon icon="material-symbols:arrow-back-ios" />
                </button>

                <span>
                    {{ announcements[currentAnnouncement] }}
                </span>

                <button
                    class="announcement_change_btn"
                    @click="nextAnnouncement"
                    aria-label="Next announcement"
                >
                    <Icon icon="material-symbols:arrow-forward-ios" />
                </button>
            </div>
        </Transition>
    </div>
</template>

<style lang="css" scoped>
.annoucement_main {
    width: 100%;
    height: 40px;
    background-color: #1c1c1c;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fffefe;
    font-size: 0.9rem;
    font-weight: 300;
    overflow: hidden;
}

.announcement_content {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 30px;
}

/* Buttons */
.announcement_change_btn {
    padding: 0;
    margin: 0;
    background-color: transparent;
    border: none;
    display: flex;
    align-items: center;
    color: rgb(155, 155, 155);
    cursor: pointer;
    transition: color 0.2s ease;
}

.announcement_change_btn:hover {
    color: #fff;
}

.announcement_change_btn svg {
    width: 16px;
    height: 16px;
}

.announcement-fade-enter-active,
.announcement-fade-leave-active {
    transition: opacity 0.35s ease;
}

.announcement-fade-enter-from,
.announcement-fade-leave-to {
    opacity: 0;
}
</style>