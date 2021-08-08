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
        <!-- 
            When you click on this button it adds the flight to the middle card, aircraft rotation list, and removes it from the flight list.  
            The button text changes from "Add to Rotation" to "Remove from Rotation" once it gets moved into the Rotation list. 
            When the button is clicked while in the Rotation list, it removes the flight from the rotation list and adds it back to the Flights list
            Every time a flight is added/removed from the Rotation list, the aircraft's utilization percentage in the aircraft list needs to be updated. 
        -->
        <button class="flight-card__button">Add to Rotation</button>
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
        border: 1px solid blue;
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
        background: blue;
        border: none;
        border-radius: 1rem;
        color: white;
        margin-bottom: 1rem;
        padding: .5rem 2rem;
    }
</style>