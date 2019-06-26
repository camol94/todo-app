<template>
    <div class="todo-filters">
        <button :class="{ active: filter == 'all' }" @click="filterAll()">All</button>
        <button :class="{ active: filter == 'active' }" @click="filterActive()">Active</button>
        <button :class="{ active: filter == 'completed' }" @click="filterCompleted()">Completed</button>
    </div>
</template>

<script>
export default {
    props: ['filter'],
    data() {        
        return {

        }
    },
    methods: {
        filterAll() {
            this.$emit('filterAll');
        },
        filterActive() {
            this.$emit('filterActive');
        },
        filterCompleted() {
            this.$emit('filterCompleted');
        }
    }
}
</script>

<style scoped>
button {
    font-size: 17px;
    background-color: white;
    color: black;
    margin: 0 5px;
    cursor: pointer;
    /* padding: 3px; */
    box-sizing: border-box;
    border: 1px solid rgb(0, 0, 0);
    border-radius: 5px;
}
button:hover {
    background: lightgreen;
}
button:focus {
    outline: none;
}
    .active {
        /* border: 1px solid green; */
        background: lightgreen;
    }
</style>