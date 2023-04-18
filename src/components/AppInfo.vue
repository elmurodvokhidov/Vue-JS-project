<template>
    <Box class="appInfo">
        <p class="fs-3 text-uppercase">Barcha kinolar soni: {{ barchaKinolar }}</p>
        <p class="fs-4 text-uppercase">Ko'rilgan kinolar soni: {{ watchedMovies }}</p>
    </Box>
</template>

<script>
import Box from "@/ui/Box.vue";
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
    },
    components: {
        Box,
    },
}
</script>

<style scoped></style>