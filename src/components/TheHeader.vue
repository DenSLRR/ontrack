<template>
    <header class="sticky top-0 z-20 flex items-center justify-between border-b bg-white p-3">
       <TheLogo @click="emit('goToTimline')"/>
       <TheHeaderProgress @click="emit('goToProgress')"/>
      
      </header>
</template>

<script setup>
    import TheLogo from './TheLogo.vue'
    import TheHeaderProgress from './TheHeaderProgress.vue';
    const emit = defineEmits(['goToTimline', 'goToProgress'])

</script>

<style  scoped>

</style>