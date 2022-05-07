<template>
    <div class="card">
        <h1>Weather forecast</h1>
        <input @keyup.enter="submit()" v-model="city" type="text" placeholder="Enter location eg Port-Louis" >
    </div>
    
    <div class="result">
        <transition name="slideleft">
            <div class="location" v-if="show">
                <h2>{{location}}</h2>
                <p>{{condition}}</p>
                <h1>{{maxtemp}}</h1>
                <p>{{maxwind}}</p>
            </div>
       </transition>
        
       <transition name="slideright">
            <div class="image">
                <img :src=image alt="" style="display: none" onload="this.style.display=''">
            </div>
        </transition>
    </div>
</template>


<script>

import axios from "axios"

const api = process.env.VUE_APP_WF_API;

export default {

    data(){
        return{
            show:true,
            city: "",
            location:"",
            condition:"",
            maxtemp:"",
            maxwind:"",
            image:""
        }
    },
    
    methods:{
        
        async submit(){
            if (!this.city){
                return
            }
            try{
                const url = `https://api.weatherapi.com/v1/forecast.json?key=${api}&q=${this.city}&days=1&aqi=no&alerts=no`
                axios
                .get(url)
                .then(response => {
                    // console.log(response)
                    this.location = response.data.location.name
                    this.condition = response.data.forecast.forecastday[0].day.condition.text
                    this.maxtemp = response.data.forecast.forecastday[0].day.maxtemp_c + '°C'
                    this.maxwind = response.data.forecast.forecastday[0].day.maxwind_kph + ' Km/h'
                    this.image =  response.data.forecast.forecastday[0].day.condition.icon
                })
                



            } catch (err) {
        if (err.response) {
          // client received an error response (5xx, 4xx)
          console.log("Server Error:", err)
        } else if (err.request) {
          // client never received a response, or request never left
          console.log("Network Error:", err)
        } else {
          console.log("Client Error:", err)
        }
            
        }
    }
    }
}
</script>

<style>
    .slideleft-enter-from{
        opacity: 0;
        transform: translateX(-160px);
    }

    .slideleft-enter-to{
        opacity: 1;
        transform: translateX(0);
    }

    .slideleft-enter-active{
        transition: all 0.2s ease;
    }
</style>