<template>
    <div class="dashboard">
        <div class="card"></div>
        <div class="card -center"></div>
        <div class="card">
            <FlightCard
                v-for="flight in this.flightDataList" 
                :key="flight.id"
                :flight="flight"
            />
        </div>
    </div>
</template>

<script>
import FlightCard from './components/FlightCard.vue'

export default {
    name: 'App',
    components: {
        FlightCard
    },
    data() {
        return {
            flightDataList: []
        };
    },
    created() {
        this.getFlightData();
    },
    methods: {
        getFlightData() {
            fetch('flights.json')
                .then(response => response.json())
                .then(data => (this.flightDataList = data));
        }
    }
}
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
