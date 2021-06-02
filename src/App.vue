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
            <todo-input @addTodo="newTodo" ref="todoInputText" />
            <button
                class="px-4 mt-4 mx-auto flex content-center 
                focus:outline-none border-b border-green-700 hover:border-b-2"
                @click="hideDone"
            >
                Filter
            </button>
            <todo-list
                :todos="todos"
                @removeTodo="remove"
                @markDone="handleDone"
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
            show: true,
            todos: [
                {
                    id: 1,
                    value: "Meu primeiro todo",
                    status: false,
                    show: true,
                },
                { id: 2, value: "Meu segundo todo", status: false, show: true },
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
                        show: true,
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
        hideDone() {
            const newTodos = [...this.todos];
            this.todos = newTodos.map((t) => {
                if (t.status) t.show = this.show;
                return t;
            });

            this.show = !this.show;
        },
    },
};
</script>
