<script setup>
    defineProps({
        temperature: Number, 
        unit: String,
    });
</script>

<template>
    <div>
        <span class="value"> {{ temperature }}</span>
        <span class="unit"> {{ unit }}</span>
    </div>
</template>

<style scoped>

</style>