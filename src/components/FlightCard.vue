<template>
    <div class="flight-card__container">
        <div class="flight-card__id">{{ flight.id }}</div>
        <div class="flight-card__details">
            <div class="flight-card__depart">
                <p class="flight-card__origin">{{ flight.origin }}</p>
                <p class="flight-card__depart-time">{{ flight.readable_departure }}</p>
            </div>
            <div class="flight-card__arrive">
                <p class="flight-card__destination">{{ flight.destination }}</p>
                <p class="flight-card__arrival-time">{{ flight.readable_arrival }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FlightCard',
    props: ['flight']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>