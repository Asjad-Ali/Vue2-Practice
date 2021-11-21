<template>
  <div  class="main m-0">
      
        <div class="col"><input type="search" name="" id="searchBar" 
        class="w-25 mt-5" placeholder="Enter city for Search" v-on:keyup.enter="submitInput"
        v-model="inputCity">
        </div>

      <div class="weather-wrap">
          <div class="location-box">
              <div class="location">{{weather.name}} , {{weather.sys.country}}</div>
              <div class="feel-like mt-2">Feels Like {{Math.round(weather.main.feels_like)}}°F</div>
          </div>
          <div class="weather-box">
              <div class="temp">{{Math.round(weather.main.temp)}}°F
                  <div class="weather">{{weather.weather[0].main}} </div>
              </div>
              
          </div>
      </div>
  </div>
</template>

<script>
import vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
vue.use(VueAxios, axios);

export default {
    name : 'weather',
    data(){
        return{
            weather : {},
            inputCity: null,
      apiKey: "2c74fe4f73b0252351d37fd80234293b",
            
        }
    },
    mounted() {
    vue.axios.get("https://api.openweathermap.org/data/2.5/weather?q=pakistan&appid=2c74fe4f73b0252351d37fd80234293b")
    .then((res) => {
        this.weather = res.data;
       console.warn(res.data);
    });
  },
    methods: {
    //weather api data fetching method
    submitInput: function () {
      vue.axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.inputCity}&appid=2c74fe4f73b0252351d37fd80234293b`
        )
        .then((res) => {
            this.weather = res.data;
          console.log(res.data);
        });
    },
  },

}
</script>

<style>
.main {
    background-image: url('../assets/weather.jpg');
    background-position: center;
    background-attachment: fixed;
    height: 95.6vh;
    padding: 10px;
}
.weather-wrap{
    margin-top: 3%;
}
.location-box .location {
  color: #000f;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 1px rgb(51, 50, 50);
}
.location-box .date {
  color: #000f;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
.weather-box {
  text-align: center;
}
.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #000f;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 3px rgba(0, 0, 0, 0.25);
  background-color:rgba(255, 255, 255, 0.52);
  border-radius: 16px;
  margin: 10px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather-box .weather {
  color: #000f;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 3px rgba(0, 0, 0, 0.25);
}
.location-box .feel-like{
  color: #000f;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
#searchBar{
    border-radius: 10px;
    padding: 3px;
    background-color: rgb(210, 212, 214);
}
#searchBar :focus{
    outline: 2px solid black;
}


</style>