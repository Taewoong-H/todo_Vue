<template>
    <div class="controller">
        <div class="select">
        <label for="order">Order</label>
        <select name="order" id="order" class="selectbox" v-model="selected" v-on:change="sortTodo">
            <option value="date-asc">Oldest</option>
            <option value="date-desc">Latest</option>
        </select>
        </div>
        <button class="clear" v-on:click="clearToDo">Clear All</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            selected: "data-asc"
        }
    },

    methods: {
        sortTodo() {
            this.$emit("sortItem", { value: this.selected });
        },

        clearToDo() {
            this.$emit("clearAll");
        }
    }
}
</script>

<style>
.controller {
    display: flex;
    justify-content: space-between;
    align-content: center;
    margin: 5rem 0;
}
</style>