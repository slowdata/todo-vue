<template>
    <ul class="mt-6 mx-auto p-2 w-4/5">
        <li v-for="todo in todos" :key="todo.id">
            <div
                v-if="todo.show"
                class="mb-4 p-2 text-gray-500 text-lg border-b flex justify-between items-center"
            >
                <span
                    :class="{
                        'line-through italic text-green-700 font-semibold':
                            todo.status,
                    }"
                    class="cursor-pointer"
                    @click="$emit('markDone', todo.id)"
                    >{{ todo.value }}</span
                >
                <button
                    class="w-8 h-8 rounded-full border text-red-600 font-bold"
                    @click.prevent="$emit('removeTodo', todo.id)"
                >
                    X
                </button>
            </div>
        </li>
    </ul>
</template>

<script>
export default {
    props: ["todos"],
};
</script>
