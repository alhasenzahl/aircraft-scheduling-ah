<template>
    <div class="rotation-card__container">
        <div class="rotation-card__id">{{ item.ident }}</div>
        <div class="rotation-card__details">
            <div class="rotation-card__depart">
                <p class="rotation-card__origin">{{ item.origin }}</p>
                <p class="rotation-card__depart-time">{{ item.readable_departure }}</p>
            </div>
            <div class="rotation-card__arrive">
                <p class="rotation-card__destination">{{ item.destination }}</p>
                <p class="rotation-card__arrival-time">{{ item.readable_arrival }}</p>
            </div>
        </div>
        <button class="rotation-card__button" @click="$emit('removeFromRotation');">Remove from Rotation</button>
    </div>
</template>

<script>
export default {
    name: 'RotationCard',
    props: ['item']
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

    .rotation-card__container {
        border: 1px solid purple;
    }

    .rotation-card__id {
        padding: 1rem 0;
    }

    .rotation-card__details {
        display: flex;
        justify-content: space-between;
    }

    .rotation-card__depart,
    .rotation-card__arrive {
        padding: 0 2rem;
    }

    .rotation-card__button {
        background: purple;
        border: none;
        border-radius: 1rem;
        color: white;
        margin-bottom: 1rem;
        padding: .5rem 2rem;
    }
</style>
