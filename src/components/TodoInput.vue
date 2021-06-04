<template>
    <form class="flex" @submit.prevent="$emit('addTodo', todo)">
        <input
            class="w-full px-2 py-2 md:py-3 rounded-md
            focus:outline-none focus:ring-2
            focus:ring-gray-300"
            type="text"
            placeholder="Insert a new to do..."
            v-model="todo"
        />
        <button
            class="ml-2 px-4 border border-gray-300 rounded-lg
        hover:text-white hover:bg-gradient-to-r
        hover:from-green-500 hover:to-green-900 "
        >
            Add
        </button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            todo: "",
        };
    },
};
</script>
