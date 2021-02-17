<template>
    <ul class="list">
        <li class="list_item" v-for="(toDoItem, index) in this.props" v-bind:key="index">
            <input type="checkbox" v-bind:id="toDoItem.item" v-bind:checked="toDoItem.completed === true" v-on:change="toggleComplete(toDoItem)" />
            <label v-bind:for="toDoItem.item" class="list_label">
                <p class="list_text">{{ toDoItem.item }}</p>
            </label>
            <p class="list_data">{{toDoItem.date}}</p>
            <button class="list_delete" v-on:click="removeToDo(toDoItem, index)">Delete</button>
        </li>
    </ul>
</template>

<script>
export default {
    props: ["props"],

    methods: {
        toggleComplete(toDoItem) {
            this.$emit("toggleItem", toDoItem);
        },

        removeToDo(toDoItem, index) {
            this.$emit("removeItem", toDoItem, index);
        }
    }

}
</script>

<style>
    .list_item {
        display: flex;
    }

    .list_item input {
        margin-top: 1.5rem;
        flex: 0.1;
    }

    .list_item label {
        flex: 2;
    }

    .list_item p {
        display: block;
        flex: 0.1;
    }

    .list_item button {
        flex: 0.1;
    }
</style>
