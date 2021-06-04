<template>
    <ul class="mt-6 mx-auto p-2 md:w-4/5">
        <li v-for="todo in todos" :key="todo.id">
            <div
                v-if="!(filter && todo.status)"
                class="mb-4 p-2 text-gray-500 text-lg border-b flex justify-between items-center"
            >
                <div
                    class="flex items-center cursor-pointer text-sm md:text-base"
                    :class="{
                        'line-through italic text-green-700 font-semibold':
                            todo.status,
                    }"
                    @click="$emit('markDone', todo.id)"
                >
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        class="h-6 w-6 mr-1"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="green"
                        v-if="todo.status"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M9 12l2 2 4-4m 6 2a 9 9 0 11-18 0 9 9 0 0118 0z"
                        />
                    </svg>
                    <span>{{ todo.value }}</span>
                </div>
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
    props: ["todos", "filter"],
};
</script>
