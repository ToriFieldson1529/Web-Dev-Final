<template>
    <div>
        <label for="zipcode">Zip Code:  </label>
        <input type="number" name="zipcode" id="zip">
        <label for="celfahr">    Celcius or Fahrenheit? </label>
        <input type="text" name="celfahr" id="celfahr">
        <input type="submit" value="Submit" @click="listening()">
    </div>  
</template>

<script>
import axios from 'axios'

export default {
    name: "WeatherChecker",
    data() {
        return {
            weather: []
        }
    },
    mounted() {
    axios
    //https://api.openweathermap.org/data/2.5/weather?zip={65706}&appid=4dff01729e9befa932e3844c8ba1a3ab
        .get("https://api.openweathermap.org/data/2.5/weather?zip=65706,us&appid=4dff01729e9befa932e3844c8ba1a3ab")
        .then((response) => {
            this.weather = response.data.main;
            console.log(response);
        });
    },

}
</script>
