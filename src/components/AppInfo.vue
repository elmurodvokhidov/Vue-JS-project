<template>
    <div class="appInfo">
        <p class="fs-3 text-uppercase">Barcha kinolar soni: {{ barchaKinolar }}</p>
        <p class="fs-4 text-uppercase">Ko'rilgan kinolar soni: {{ watchedMovies }}</p>
    </div>
</template>

<script>
export default {
    props: {
        barchaKinolar: {
            type: Number,
            required: true,
        },
        watchedMovies: {
            type: Number,
            required: true,
        }
    }
}
</script>

<style scoped>
.appInfo {
    padding: 1.5rem;
    border-radius: 4px;
    background-color: #fcfaf4;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>