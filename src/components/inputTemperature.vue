<script setup>
    defineProps({
        name : String, 
        modelValue : Number, 
    });
</script>

<template>
  <p class="title-temp">{{ name }}</p>
  <input type="number" v-model="modelValue" /> 
  <br>
</template>

<style scoped>

</style>