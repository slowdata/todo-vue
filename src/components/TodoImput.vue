<template>
    <form action="" class="flex">
        <input
            class="w-full px-2 py-3 rounded-md
            focus:outline-none focus:ring-2
            focus:ring-gray-300"
            type="text"
            placeholder="Insert a new todo"
            v-bind="todo"
        />
        <button
            class="ml-2 px-4 border border-gray-300 rounded-lg
        hover:bg-green-600 hover:text-white"
        >
            Add
        </button>
    </form>
</template>

<script>
export default {};
</script>
