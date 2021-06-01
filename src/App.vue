<template>
    <div
        class="flex flex-col items-center mt-14 
      "
    >
        <h1 class="text-4xl font-mono mb-10 text-gray-700">
            TO DO's
        </h1>
        <card />
    </div>
</template>

<script>
import Card from "./components/Card";
export default {
    name: "App",
    components: { Card },
};
</script>
