<template>
    <ul class="list">
        <li class="list_item">
            <input type="checkbox" id="list-item-1" />
            <label for="list-item-1">
                <p class="list_text">Smile! :)</p>
            </label>
            <p class="list_data">5/26</p>
            <button class="list_delete">Delete</button>
        </li>
    </ul>
</template>

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
