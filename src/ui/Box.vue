<template>
    <div class="box">
        <slot></slot>
    </div>
</template>
<script>
export default {

}
</script>
<style scoped>
.box {
    padding: 1.5rem;
    border-radius: 4px;
    background-color: #fcfaf4;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>