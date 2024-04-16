<script setup>
  import AppTemperature from './components/AppTemperature.vue';
  import inputTemperature from './components/inputTemperature.vue';
  import { computed, ref, watch } from 'vue';

  const tempSI = defineModel('tempSI', {type: Number, default: 273.15});

  const tempCel = defineModel('tempCel', {
    type : Number, 
    default: 0,
    get : () => tempSI.value - 273.15,
    set : (newValue) => {
      tempSI.value = newValue + 273.15;
    }
  });

  const tempFar = defineModel('tempFar', {
    type : Number,
    default : 0,
    get : () => tempSI.value * 9/5 - 459.67,
    set : (newValue) => {
      tempSI.value =  (newValue + 459.67) * 5/9;
    }
  });

  // const tempCel = computed({
  //  get : () => arrondir(tempSI.value - 273.15),
  //  set : (newValue) => {
  //    tempSI.value = arrondir(newValue + 273.15);
  //  }
  // });

  //const tempFar = computed({
  //  get : () => arrondir(tempSI.value * 9/5 - 459.67),
  //  set : (newValue) => {
  //    tempSI.value =  arrondir((newValue + 459.67) * 5/9);
  //  }
  // });

  // watch(tempSI, (newVal) => {
  //  console.log(
  //    `Kelvin: ${newVal}, Celsius: ${tempCel.value}, Fahrenheit: ${tempFar.value}`
  // )
  // });

 // setInterval(() => {
 //   tempCel.value = Math.random() * 100;
 // }, 1000);

</script>

<template>
  <h2>Temperature Converter</h2>

  <inputTemperature unit="Kelvin" v-model="tempSI" step="0.1"/>
  <inputTemperature unit="Celsius" v-model="tempCel" step="0.1"/>
  <inputTemperature unit="Farenheit" v-model="tempFar" step="0.1"/>

  <p v-if="tempSI < 0">
    Votre degré Kelvin est en dessous de 0... Are you sure about that ? 
  </p>

  <!-- p class="title-temp">Kelvin</p>
  <input type="number" v-model="tempSI" /> 
  <br>

  <p class="title-temp">Celsius</p>
  <input type="number" v-model="tempCel" /> 
  <br>

  <p class="title-temp">Farenheit</p>
  <input type="number" v-model="tempFar" /> 
  <br>

  <br>

  <p v-if="tempSI < 0">
    Votre degré Kelvin est en dessous de 0... Are you sure about that ? 
  </p -->

  <!-- AppTemperature :temperature="tempSI" unit="°K"/>
  <AppTemperature :temperature="tempCel" unit="°C" />
  <AppTemperature :temperature="tempFar" unit="°F"/ -->
</template>

<style scoped>

</style>
