<template>
    <Box class="movieAddForm">
        <h3>Yangi kino qo'shish</h3>
        <form action="#" class="d-flex addForm" @submit.prevent>
            <!-- Birinchi input || Kino nomi -->
            <Input class="newMovie" name="newMovie" id="newMovie" placeholder="Qanday kino?" v-model="name"></Input>
            <!-- Ikkinchi input || Ko'rilgan soni -->
            <Input type="number" class="newMovie" name="newMovie1" id="newMovie1" placeholder="Necha marta ko'rilgan?"
                v-model="view"></Input>
            <!-- Qo'shish tugmasi -->
            <PrimaryBtn class="btn-outline-dark" type="button" @click="addItem">Qo'shish</PrimaryBtn>
        </form>
    </Box>
</template>
<script>
import PrimaryBtn from "@/ui/PrimaryBtn.vue";
import Box from "../ui/Box.vue";
import Input from "../ui/Input.vue";

export default {
    components: {
        PrimaryBtn,
        Box,
        Input,
    },
    data() {
        return {
            name: '',
            view: '',
        }
    },
    methods: {
        // Yangi ma'lumot qo'shish funksiyasi va propslar
        addItem() {
            // Inputda ma'lumot bor ekanligini tekshirish
            if (!this.name || !this.view) return
            // Inputdan keladigan ma'lumotlarni saqlab turuvchi obyekt
            const newItem = {
                name: this.name,
                view: this.view,
                favorite: false,
                like: false,
                id: Date.now(),
            }
            // parent componentiga child componentdan jo'natiladigan propslar
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
    border-radius: 4px;
}
</style>