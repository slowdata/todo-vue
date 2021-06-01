<template>
    <div
        class="mt-14 flex flex-col
      justify-center items-center"
    >
        <h1 class="text-4xl mb-10">
            TODO's
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
