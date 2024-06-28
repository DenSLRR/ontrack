<template>
    <TheHeader @go-to-progress="goTo(PAGE_PROGRESS)" @go-to-timline="goTo(PAGE_TIMELINE)" />

    <main class="flex flex-grow flex-col">
        <TheTimeline v-show="currentPage === PAGE_TIMELINE" />
        <TheActivities v-show="currentPage === PAGE_ACTIVITIES" />
        <TheProgress v-show="currentPage === PAGE_PROGRESS" />
    </main>

    <TheNav :current-page="currentPage" @page-change="onPageChange" />
</template>

<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheNav from "./components/TheNav.vue";
import TheTimeline from "./pages/TheTimeline.vue";
import TheActivities from "./pages/TheActivities.vue";
import TheProgress from "./pages/TheProgress.vue";
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from "./constants.js";
import { ref, reactive } from "vue";
import {normalizePageHash} from './functions'

const currentPage = ref(normalizePageHash());

function goTo(page) {
    currentPage.value = page
}

const onPageChange = (page) => {
    currentPage.value = page;
};
</script>

<style></style>
