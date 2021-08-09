<template>
    <div class="dashboard">
        <div class="card">
            <AircraftCard
                v-for="aircraft in this.aircraftDataList" 
                :key="aircraft.ident"
                :aircraft="aircraft"
                :util="this.utilizationPercent"
            />
        </div>
        <div class="card -center">
            <RotationCard
                v-for="item in this.rotationDataList" 
                :key="item.ident"
                :item="item"
                @removeFromRotation="removeCard(item)"
            />
        </div>
        <div class="card">
            <FlightCard
                v-for="flight in this.flightDataList" 
                :key="flight.ident"
                :flight="flight"
                @addToRotation="addCard(flight)"
            />
        </div>
    </div>
</template>

<script>
import FlightCard from './components/FlightCard.vue'
import AircraftCard from './components/AircraftCard.vue'
import RotationCard from './components/RotationCard.vue'

export default {
    name: 'App',
    components: {
        FlightCard,
        AircraftCard,
        RotationCard
    },
    data() {
        return {
            flightDataList: [],
            aircraftDataList: [],
            rotationDataList: [],
            utilizationTime: 0,
            utilizationPercent: 0
        };
    },
    created() {
        this.getFlightData();
        this.getAircraftData();
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
        },

        addCard(card) {
            this.flightDataList.splice(this.flightDataList.indexOf(card), 1);
            this.rotationDataList.push(card);

            this.addSeconds(card);
        },

        removeCard(card) {
            this.rotationDataList.splice(this.rotationDataList.indexOf(card), 1);
            this.flightDataList.unshift(card);

            this.subtractSeconds(card);
        },

        addSeconds(card) {
            this.utilizationTime += card.arrivaltime - card.departuretime;

            this.utilizationPercent = Math.round((this.utilizationTime / 86400) * 100);
        },

        subtractSeconds(card) {
            this.utilizationTime -= (card.arrivaltime - card.departuretime);

            this.utilizationPercent = Math.round((this.utilizationTime / 86400) * 100);
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
