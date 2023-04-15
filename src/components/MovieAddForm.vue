<template>
    <div class="movieAddForm">
        <h3>Yangi kino qo'shish</h3>
        <form action="#" class="d-flex addForm" @submit.prevent>
            <input type="text" class="form-control newMovie" name="newMovie" id="newMovie" placeholder="Qanday kino?"
                :value="name" @input="name = $event.target.value">
            <input type="number" class="form-control newMovie" name="newMovie1" id="newMovie1"
                placeholder="Necha marta ko'rilgan?" :value="view" @input="view = $event.target.value">
            <button class="btn btn-outline-dark" type="button" @click="addItem">Qo'shish</button>
        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            name: '',
            view: '',
        }
    },
    methods: {
        addItem() {
            const newItem = {
                name: this.name,
                view: this.view,
                favorite: false,
                like: false,
            }
            this.$emit('createItem', newItem)
            this.name = ''
            this.view = ''
        },
    },
}
</script>
<style scoped>
.movieAddForm {
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>