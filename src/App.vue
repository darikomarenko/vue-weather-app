<script>
import axios from 'axios';
export default {
  data() {
    return {
      city: "",
      error: "",
      info: null,
    }
  },
  methods: {
    getWeather() {
      if(this.city.trim().length < 2){
        this.error = 'Enter a valid city name'
        return false
      }
      this.error = ""
      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=b5c3d460e3c1a01dfec40d04c8e449f5`)
      .then(res => (this.info = res.data))
    }
  },
  computed: {
    showTemp() {
      return "Temperature is " + this.info.main.temp
    },
    showFeelsLikeTemp() {
      return "Temperature feels like " + this.info.main.feels_like
    },
    showMinTemp() {
      return "Min temperature is " + this.info.main.temp_min
    },
    showMaxTemp() {
      return "Max temperature is " + this.info.main.temp_max
    },
  }
}
</script>

<template>
  <div className="wrapper">
    <h1>Weather App </h1>
    <p>Check on weather in {{ city == '' ? 'any city' : city}}</p>
    <input type="text" v-model="city" placeholder="Enter city">
    <button v-if="city != ''" @click="getWeather()">Check weather</button>
    <button disabled v-else>Enter city</button>
    <p class="error">{{ error }}</p>
    <div v-if="info != null">
      <p> {{ showTemp }}</p>
      <p> {{ showFeelsLikeTemp }}</p>
      <p> {{ showMinTemp }}</p>
      <p> {{ showMaxTemp }}</p>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: #94bbe9;
  padding: 20px;
  text-align: center;
  color: black;
}

.wrapper h1 {
  margin-top: 50px;
  font-size: 36px;
}

.wrapper p {
  margin-top: 20px;
}

.wrapper input {
  margin: 10px;
  background: white;
  color: #6e2d7d;
  font-size: 14px;
  border: 2px solid #6e2d7d;
  border-radius: 10px;
  padding: 10px 15px;
  outline: none;
}

.wrapper input:focus {
  border: 2px solid #6e2d7d;
}

.wrapper button {
  background: #6e2d7d;
  color: white;
  border-radius: 10px;
  border: 2px solid #6e2d7d;
  padding: 10px 15px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  background: white;
  color: #6e2d7d;
}

.wrapper button:disabled {
  background: grey;
  color: white;
  cursor: not-allowed;
}

.error {
  color: #d03939;
}

p {
  font-size: 16px;
}
</style>
