<template>
    <div class="btn-group">
        <button class="btn" type="button" @click="filterHandler('all')" :class="[filterName === 'all' ?
            'btn-dark' : 'btn-outline-dark']">Barcha kinolar</button>
        <button class="btn" type="button" @click="filterHandler('popular')" :class="[filterName === 'popular' ?
            'btn-dark' : 'btn-outline-dark']">Mashxur kinolar</button>
        <button class="btn" type="button" @click="filterHandler('mostView')" :class="[filterName === 'mostView' ?
            'btn-dark' : 'btn-outline-dark']">Eng ko'p ko'rilgan
            kinolar</button>
    </div>
</template>
<script>
export default {
    props: {
        updFilterHandler: {
            type: Function,
            required: true,
        },
        filterName: {
            type: String,
            required: true,
        }
    },
    data() {
        return {
            filter: 'all',
        }
    },
    methods: {
        filterHandler(filter) {
            this.filter = filter
            this.updFilterHandler(this.filter)
        }
    },
}
</script>
<style scoped></style>