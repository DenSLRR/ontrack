<template>
    <div class="mt-7">
        <ul>
            <TimelineItem v-for="timelineItem in timelineItems" :key="timelineItem.hour" :timeline-item="timelineItem"/>
             
        </ul>
    </div>
</template>

<script setup>

import TimelineItem from "../components/TimelineItem.vue";
import { isTimeLineItemValid } from "@/validators";

// defineProps(['timelineItems'])
defineProps({
  timelineItems: {
    required: true,
    type: Array,
    validator(timelineItems) {
      return timelineItems.every(isTimeLineItemValid)
    }
  }
})
</script>

<style scoped></style>
