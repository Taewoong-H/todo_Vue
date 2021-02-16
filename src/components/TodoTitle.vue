<template>
    <div class="title">
        <p class="title_message">{{message}}</p>
        <p class="title_task">
            You've got <span class="title_task_total">{{taskTotal}}</span> tasks today.
        </p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: "Hello",
            taskTotal: 5
        };
    }
}
</script>

<style>
.title {
    margin: 0 auto;
    letter-spacing: 0.03rem;
    color: #aaa;
}

.title_message {
    font-size: 1.6rem;
}

.title_task {
    margin-top: 3.5rem;
    margin-bottom: 5rem;
    font-weight: bold;
}


</style>