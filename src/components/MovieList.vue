<template>
    <ul class="list-group movieList">
        <MovieItem v-for="(item, index) in movies" :key="index" v-bind:property="item" />
    </ul>
</template>
<script>
import MovieItem from './MovieItem.vue';

export default {
    components: { MovieItem },
    data() {
        return {
            movies: [
                {
                    name: 'Man in black',
                    view: 787,
                    favorite: false,
                    like: true,
                },
                {
                    name: 'Titanic',
                    view: 145,
                    favorite: true,
                    like: false,
                },
                {
                    name: 'Avatar',
                    view: 511,
                    favorite: true,
                    like: true,
                },
            ]
        }
    },
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