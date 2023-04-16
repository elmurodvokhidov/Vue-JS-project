<template>
    <ul class="list-group movieList">
        <MovieItem v-for="(item, index) in movies" :key="item.id" v-bind:property="item"
            @onLike="$emit('onLike', item.id)" />
    </ul>
</template>
<script>
import MovieItem from './MovieItem.vue';

export default {
    components: { MovieItem },
    props: {
        movies: {
            type: Array,
            required: true,
        }
    }
}
</script>
<style scoped>
.movieList {
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>