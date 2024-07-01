<template>
    <nav class="sticky bottom-0 z-10 bg-white">
        <ul class="flex items-center justify-around border-t">
            <NavItem
                v-for="(icon, page) in NAV_ITEMS"
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
import NavItem from "./NavItem.vue";
import { NAV_ITEMS } from "@/constants";
import { isPageValid } from "@/validators";
const props = defineProps({
    currentPage: {
        required: true,
        type: String,
        validator: isPageValid
    }
});

const emits = defineEmits(["page-change"]);



const handleClick = (page) => {
    emits("page-change", page);
};
</script>

<style scoped></style>
