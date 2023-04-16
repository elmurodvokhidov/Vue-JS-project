<template>
    <input @input="changeHandler" :value="term" class="form-control searchInput" type="text" name="search" id="search"
        placeholder="Kinolarni qidirish">
</template>
<script>
export default {
    props: {
        updTermHandler: {
            type: Function,
            required: true,
        }
    },
    data() {
        return {
            term: '',
        }
    },
    methods: {
        changeHandler(e) {
            this.term = e.target.value
            this.updTermHandler(this.term)
        }
    },
}
</script>
<style scoped>
.searchInput {
    margin-bottom: 1.5rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>