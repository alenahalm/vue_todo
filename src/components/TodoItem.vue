<template>
    <li>
        <span v-bind:class="{ done: todo.completed }">
            <input type="checkbox" v-on:change="td.completed = !td.completed">
            {{ todo.title }}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            td: this.todo,
        }
    },
}
</script>

<style scoped>
li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
}

.rm {
    background: red;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
}

input {
    margin-right: 1rem;
}

.done {
    text-decoration: line-through;
}
</style>