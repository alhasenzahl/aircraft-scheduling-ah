<template>
    <div class="headers__wrap">
        <div class="panel__header">
            <h2 class="panel__title">Aircrafts</h2>
        </div>
        <div class="panel__header">
            <h2 class="panel__title">Rotation</h2>
        </div>
        <div class="panel__header">
            <h2 class="panel__title">Flights</h2>
        </div>
    </div>
    <div class="dashboard">
        <div class="panel">
            <div class="panel__inner">
                <AircraftCard
                    v-for="aircraft in this.aircraftDataList" 
                    :key="aircraft.ident"
                    :aircraft="aircraft"
                    :util="this.utilizationPercent"
                />
            </div>
        </div>
        <div class="panel -center">
            <div class="panel__inner">
                <RotationCard
                    v-for="item in this.rotationDataList" 
                    :key="item.ident"
                    :item="item"
                    @removeFromRotation="removeCard(item)"
                />
            </div>
        </div>
        <div class="panel">
            <div class="panel__inner">
                <FlightCard
                    v-for="flight in this.flightDataList" 
                    :key="flight.ident"
                    :flight="flight"
                    @addToRotation="addCard(flight)"
                />
            </div>
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
    body {
        background: #FCFAF9; 
    }

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    .headers__wrap {
        display: flex;
        justify-content: space-between;
    }

    .panel {
        border: 2px solid #5E5E5E;
        border-radius: .5rem;
        width: 24%;
        height: calc(100vh - 8rem);
        overflow: scroll;
        display: inline-block;
        vertical-align: top;
        background: #F3D3BD;
        margin-right: 2%;
    }

    .panel:last-of-type {
        margin-right: 0;
    }

    .panel.-center {
        width: 46%;
    }

    .panel__header {
        width: 25%;
    }

    .panel__title {
        color: #333;
        margin: 0;
        padding: 2rem 0;
    }

    .panel__inner {
        margin-top: 1rem;
    }
</style>
