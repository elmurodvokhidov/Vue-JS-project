<template>
    <Input v-model="term" @input="changeHandler" class="searchInput" name="search" id="search"
        placeholder="Kinolarni qidirish"></Input>
</template>
<script>
import Input from '../ui/Input.vue';

export default {
    props: {
        updTermHandler: {
            type: Function,
            required: true,
        }
    },
    data() {
        return {
            term: "",
        };
    },
    methods: {
        changeHandler(e) {
            this.term = e.target.value;
            this.updTermHandler(this.term);
        }
    },
    components: { Input },
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