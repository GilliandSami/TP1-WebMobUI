<script setup>
  const arrondir = (valeur) => {
    const valeur2 = parseFloat(valeur).toFixed(2);
    return parseFloat(valeur2);
  } 

    const props = defineProps({
        unit : {
          type: [Boolean, String],
          required: false,
        },
        decimal: {
          type: Number,
          required: false,
          default: 2,
        }
    });

    defineOptions({
      inheritAttrs : false
    });

    const model = defineModel({
      get: () => {
        return arrondir(props.modelValue);
      }, 
    });
</script>

<template>
    <p class="title-temp"> {{ unit }}</p>
    <input type="number" v-model="model" v-bind="$attrs" /> 
</template>

<style scoped>

</style>