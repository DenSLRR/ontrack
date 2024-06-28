<template>
    <nav class="sticky bottom-0 z-10 bg-white">
        <ul class="flex items-center justify-around border-t">
            <NavItem
                v-for="(icon, page) in navItems"
                :href="`#${page}`"
                :key="page"
                :class="{
                    'bg-gray-200 pointer-events-none': page === currentPage,
                }"
                @click="() => handleClick(page)"
            >
                <component :is="icon" class="h-6 w-6" /> {{ page }}
            </NavItem>
        </ul>
    </nav>
</template>

<script setup>
import {
    ClockIcon,
    ListBulletIcon,
    ChartBarIcon,
} from "@heroicons/vue/24/outline";
import NavItem from "./NavItem.vue";
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from "../constants";

const props = defineProps(["currentPage"]);

const emits = defineEmits(["page-change"]);

const navItems = {
    [PAGE_TIMELINE]: ClockIcon,
    [PAGE_ACTIVITIES]: ListBulletIcon,
    [PAGE_PROGRESS]: ChartBarIcon,
};

const handleClick = (page) => {
    emits("page-change", page);
};
</script>

<style scoped></style>
