<template>
    <li class="list-group-item d-flex justify-content-between"
        :class="[{ like: property.like }, { favorite: property.favorite }]">
        <span class="list-group-item-label">{{ property.name }}</span>
        <input type="text" class="list-group-item-input" :value="property.view">
        <div class="d-flex justify-content-center align-items-center">
            <button class="btn-cookie btn-sm" type="button"><i class="fas fa-cookie"></i></button>
            <button class="btn-trash btn-sm" type="button"><i class="fas fa-trash"></i></button>
            <i class="fas fa-star"></i>
        </div>
    </li>
</template>
<script>
export default {
    props: {
        property: {
            type: Object,
            required: true,
        }
    }
}
</script>
<style scoped>
.list-group-item {
    padding: 15px 20px;
    border: none;
    background-color: rgba(255, 255, 255, 0);
    border-bottom: 1px solid black;
}

.list-group-item:last-child {
    border-bottom: none;
}

.list-group-item span {
    width: 550px;
    line-height: 35px;
    font-size: 20px;
    cursor: pointer;
}

.list-group-item input {
    line-height: 35px;
    font-size: 20px;
    border: none;
    outline: none;
    text-align: center;
}

.list-group-item button {
    width: 35px;
    height: 35px;
    margin: 3px;
    font-size: 17px;
    border: none;
    cursor: pointer;
}

.list-group-item .btn-cookie {
    color: #e09f3e;
}

.list-group-item .btn-trash {
    color: #e5383b;
}

.list-group-item .fa-star {
    width: 35px;
    height: 35px;
    text-align: center;
    line-height: 35px;
    font-size: 16px;
    color: #ffd700;
    transition: .3s all;
    transform: translateX(30px);
    opacity: 0;
}

.list-group-item.like .fa-star {
    transform: translateX(0);
    opacity: 1;
}

.list-group-item.favorite .list-group-item-label,
.list-group-item.favorite .list-group-item-input {
    color: #e09f3e;
}
</style>