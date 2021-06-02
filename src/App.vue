<template>
    <div
        class="w-5/6 max-w-2xl mx-auto mt-10
      "
    >
        <h1
            class="mb-10 text-center text-4xl font-mono font-semibold text-gray-700"
        >
            <span class="text-green-600">T</span
            ><span class="text-green-900">O</span> DO's
        </h1>

        <card>
            <todo-imput />
            <ul>
                <li v-for="todo in todos" :key="todo.id">{{ todo.value }}</li>
            </ul>
        </card>
    </div>
</template>

<script>
import Card from "./components/Card";
import TodoImput from "./components/TodoImput";

export default {
    name: "App",
    components: {
        Card,
        TodoImput,
    },
    data() {
        return {
            todos: [
                { id: 1, value: "Meu primeiro todo" },
                { id: 2, value: "Meu segundo todo" },
            ],
        };
    },
};
</script>
