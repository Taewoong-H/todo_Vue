<template>
    <div class="controller">
        <div class="select">
        <label for="order">Order</label>
        <select name="order" id="order" class="selectbox">
            <option value="date-asc">Date Ascending</option>
            <option value="date-desc">Date Descending</option>
            <option value="name-asc">Name Ascending</option>
            <option value="name-desc">Name Descending</option>
        </select>
        </div>
        <button class="clear">Clear All</button>
    </div>
</template>

<style>
.controller {
    display: flex;
    justify-content: space-between;
    align-content: center;
    margin: 5rem 0;
}
</style>