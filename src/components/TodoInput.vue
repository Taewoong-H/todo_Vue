<template>
    <div class="add">
        <input type="text" class="add_input" placeholder="Enter your task" v-model="newToDoItem" v-on:keyup.enter="addToDoItem"/>
        <button class="add_button" v-on:click="addToDoItem">Add</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newToDoItem: ''
        };
    },

    methods: {
        addToDoItem() {
            if (this.newToDoItem) {
                this.$emit("addItem", this.newToDoItem);
                this.clearInput();
            }
        },

        clearInput() {
            this.newToDoItem = '';
        }
    }
}
</script>