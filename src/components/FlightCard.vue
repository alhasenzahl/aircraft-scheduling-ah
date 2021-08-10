<template>
    <div class="flight-card__container">
        <div class="flight-card__id">{{ flight.ident }}</div>
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
        <button class="flight-card__button" @click="$emit('addToRotation', flight);">Add to Rotation</button>
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

    .flight-card__container {
        background: #FCFAF9;
        color: #333;
        border-radius: .5rem;
        margin: 1rem;
    }

    .flight-card__id {
        padding: 1rem 0;
    }

    .flight-card__details {
        display: flex;
        justify-content: space-between;
    }

    .flight-card__depart,
    .flight-card__arrive {
        padding: 0 2rem;
    }

    .flight-card__button {
        background: #48E5C2;
        border: none;
        border-radius: 1rem;
        color: #333;
        margin-bottom: 1rem;
        padding: .5rem 2rem;
    }
</style>