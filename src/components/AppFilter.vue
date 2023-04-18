<template>
    <div class="btn-group">
        <PrimaryBtn v-for="item in filterBtn" :key="item.name"
            :class="[filterName === item.name ? 'btn-dark' : 'btn-outline-dark']" @click="filterHandler(item.name)">{{
                item.title
            }}</PrimaryBtn>
    </div>
</template>
<script>
import PrimaryBtn from "@/ui/PrimaryBtn.vue";
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
    components: {
        PrimaryBtn,
    },
    data() {
        return {
            filter: 'all',
            filterBtn: [
                {
                    title: 'Barcha kinolar',
                    name: 'all',
                },
                {
                    title: 'Mashxur kinolar',
                    name: 'popular',
                },
                {
                    title: "Eng ko'p ko'rilgan",
                    name: 'mostView',
                },
            ]
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