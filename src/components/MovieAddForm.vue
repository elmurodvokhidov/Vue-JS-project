<template>
    <div class="movieAddForm">
        <h3>Yangi kino qo'shish</h3>
        <form action="#" class="d-flex addForm">
            <input type="text" class="form-control newMovie" name="newMovie" id="newMovie" placeholder="Qanday kino?">
            <input type="text" class="form-control newMovie" name="newMovie1" id="newMovie1"
                placeholder="Necha marta ko'rilgan?">
            <button class="btn btn-outline-dark" type="button">Qo'shish</button>
        </form>
    </div>
</template>
<script>
export default {

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