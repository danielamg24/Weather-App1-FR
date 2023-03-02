<template>
<div id="app">
  
<main>

    <h1>L'Appli Météo</h1>
    <br>
    <h3>{{ dateBuilder() }}</h3>
  
  
  <div class="searchbox">
    <input 
    v-model="data.city"
    @keyup.enter="getWeather"
    placeholder="Rechercher..."
    type="text"
    class="search-bar">
  </div>

  
  <div 
  v-if="data.weather"
  class="weather">
  <h1>{{ Math.round (data.weather.main.temp) }}°C</h1>
  <h2>{{ data.weather.weather[0].description }}</h2>
  </div>

</main>

</div>
</template>


<script>

import {reactive} from 'vue'; 
import axios from 'axios';




export default {
  name: 'HelloWorld',
  setup(){
let data = reactive ({
  city: '', 
  weather: null
})

const apiUrl = 'http://localhost:3000/'; 


const getWeather = () =>{
      axios(`${apiUrl}?q=${data.city}&units=metric&lang=fr`)
      .then (response => {
      data.weather = response.data
      // console.log(response.data)
 })
}; 

 const dateBuilder = () =>{
     let days = ['Dimanche', 'Lundi' , 'Mardi', 'Mercredi' , 'Jeudi' , 'Vendredi' , 'Samedi'];
     let months = ['Janvier', 'Février', 'Mars', 'Avril' , 'Mai' , 'Juin' , 'Juillet', 'Août', 'Septembre', 'Octobre', 'Novembre', 'Décembre'];

     let d = new Date(); 
     let day = days [d.getDay()]; 
     let date = d.getDate();
     let month = months [d.getMonth()];
     let year = d.getFullYear(); 

     return `${day} ${date} ${month} ${year}`;
 }; 


return {
  data, 
  getWeather,
  dateBuilder
}
  }
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

main{
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75)) ;
  min-height: 100vh;
  padding: 25px; 
}

 .search-bar{
  appearance: none;
  background-color: rgba(255,255,255, 0.5);
  background: none;
  border-radius: 10px;
  border: none; 
  box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.30);
  color: #fff; 
  display: block;
  font-family: 'Quicksand Light', sans-serif;
  font-size: 20px; 
  margin: auto;
  outline: none; 
  padding: 15px;
  width: 50%;
}

.searchbox {
  padding: 100px 0px 100px 0px;
}

.weather h1{
  font-size: 90px;
}

.weather h2{
  font-size: 30px; 
  padding-top: 10px; 
  text-transform: uppercase;
}

</style>
