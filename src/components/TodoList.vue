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
            toDoItem.completed = !toDoItem.completed;
            localStorage.setItem(toDoItem.item, JSON.stringify(toDoItem));
        },

        removeToDo(toDoItem, index) {
            localStorage.removeItem(toDoItem.item);
            this.toDoItems.splice(index, 1);
        }
    }

}
</script>

<style>
    .list_item {
        display: flex;
    }

    .list_item input {
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
