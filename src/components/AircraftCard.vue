<template>
    <div class="aircraft-card__container">
        <div class="aircraft-card__id">{{ aircraft.ident }}</div>
        <div class="aircraft-card__util">{{ util }}%</div>
    </div>
</template>

<script>
export default {
    name: 'AircraftCard',
    props: ['aircraft', 'util']
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

    .aircraft-card__container {
        background: #FCFAF9;
        color: #333;
        border-radius: .5rem;
        margin: 1rem;
        padding: 1rem 0;
    }

    .aircraft-card__id {
        margin-bottom: 1rem;
    }

    .aircraft-card__util {
        color: #48E5C2;
        font-size: 1.5rem;
        font-weight: bold;
    }
</style>
