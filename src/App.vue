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
};
</script>
