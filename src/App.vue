<template>
    <div class="dashboard">
        <div class="card">
            <AircraftCard
                v-for="aircraft in this.aircraftDataList" 
                :key="aircraft.ident"
                :aircraft="aircraft"
            />
        </div>
        <div class="card -center"></div>
        <div class="card">
            <FlightCard
                v-for="flight in this.flightDataList" 
                :key="flight.ident"
                :flight="flight"
            />
        </div>
    </div>
</template>

<script>
import FlightCard from './components/FlightCard.vue'
import AircraftCard from './components/AircraftCard.vue'

export default {
    name: 'App',
    components: {
        FlightCard,
        AircraftCard
    },
    data() {
        return {
            flightDataList: [],
            aircraftDataList: []
        };
    },
    created() {
        this.getFlightData();
        this.getAircraftData()
    },
    methods: {
        getFlightData() {
            fetch('flights.json')
                .then(response => response.json())
                .then(data => (this.flightDataList = data));
        },

        getAircraftData() {
            fetch('aircrafts.json')
                .then(response => response.json())
                .then(data => (this.aircraftDataList = data));
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

    .card {
        width: 33%;
        height: 100vh;
        overflow: scroll;
        display: inline-block;
        vertical-align: top;
        border: 1px solid red;
    }
</style>
