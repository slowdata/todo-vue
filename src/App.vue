<template>
    <div
        class="h-screen sm:w-5/6 px-2 max-w-2xl -mt-14 mx-auto flex flex-col justify-center
      "
    >
        <h1
            class="mb-10 text-center text-4xl font-mono font-semibold text-gray-700"
        >
            <span class="text-green-600">T</span
            ><span class="text-green-900">O</span> DO's
        </h1>

        <card>
            <todo-input @addTodo="newTodo" ref="todoInputText" />
            <div class="mt-6 w-1/2 mx-auto flex justify-evenly">
                <button
                    class="py-1 px-4 hover:font-semibold focus:outline-none"
                    :class="{ 'border-b border-green-600 ': filter }"
                    @click="toggleFilter"
                >
                    Filter
                </button>
                <button
                    class="py-1 px-4 hover:font-semibold focus:outline-none"
                    :class="{ 'border-b border-green-600 ': order }"
                    @click="toggleOrder"
                >
                    Order
                </button>
            </div>
            <todo-list
                :todos="todos"
                @removeTodo="remove"
                @markDone="handleDone"
                :filter="filter"
            />
        </card>
    </div>
</template>

<script>
import Card from "./components/Card";
import TodoInput from "./components/TodoInput";
import TodoList from "./components/TodoList";

export default {
    name: "App",
    components: {
        Card,
        TodoInput,
        TodoList,
    },
    data() {
        return {
            filter: false,
            order: false,
            todos: [
                {
                    id: 1,
                    value: "Turn on the computer.",
                    status: false,
                    created: new Date("Thu, 03 Jun 2021 09:00:00 GMT"),
                },
                {
                    id: 2,
                    value: "Connect to the internet.",
                    status: false,
                    created: new Date("Thu, 03 Jun 2021 11:00:00 GMT"),
                },
            ],
        };
    },
    methods: {
        newTodo(value) {
            if (value) {
                const newTodos = [
                    ...this.todos,
                    {
                        id: this.todos.length + 1,
                        value,
                        status: false,
                        created: new Date().toUTCString(),
                    },
                ];

                this.todos = newTodos;
                this.$refs.todoInputText.todo = "";
            }
        },
        remove(id) {
            const newTodos = [...this.todos];
            this.todos = newTodos.filter((t) => t.id !== id);
        },
        handleDone(id) {
            const newTodos = [...this.todos];
            this.todos = newTodos.map((t) => {
                if (t.id === id) {
                    t.status = !t.status;
                    return t;
                }
                return t;
            });
        },
        toggleFilter() {
            this.filter = !this.filter;
        },
        toggleOrder() {
            const newTodos = [...this.todos];
            this.todos = newTodos.sort((t, newt) => {
                if (this.order) {
                    return new Date(t.created) - new Date(newt.created);
                } else {
                    return new Date(newt.created) - new Date(t.created);
                }
            });
            this.order = !this.order;
        },
    },
};
</script>
