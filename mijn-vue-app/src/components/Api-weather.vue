<template>
  <input type="text" v-model="city" />
  <input type="button" value="ADD" @click="getWeather" />
  <p>Het is {{weather}} graden in: {{city}}</p>
</template>

<script setup>
import { ref } from 'vue';

const city = ref('London');
const weather = ref("");

 const apiKey = process.env.VUE_APP_WEATHER_API_KEY; // Zorg ervoor dat je API-sleutel correct is ingesteld

async function getWeather() {
  try {
    const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&appid=${apiKey}&units=metric`);
    if(response.ok){
    const waitedResponse = await response.json();
    weather.value = waitedResponse.main.temp}
    else{
      console.error("No connection with the server.")
    }
  }
  catch (e){
    console.error(e)
  }
}
</script>

