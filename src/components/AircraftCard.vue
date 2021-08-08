<template>
    <div class="aircraft-card__container">
        <div class="aircraft-card__id">{{ aircraft.ident }}</div>
    </div>
</template>

<script>
export default {
    name: 'AircraftCard',
    props: ['aircraft']
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
        border: 1px solid green;
    }

    .aircraft-card__id {
        padding: 1rem 0;
    }
</style>
