<template>
    <div class="container">
        <div class="row">
            <div class="list-name">
                <h1>{{ listName }}</h1>
            </div>
        </div>
        <div class="create-todo">
            <create-todo @on-new-todo="addTodo($event)"/>
        </div>
        <div class="row">
            <div class="list-group">
                <ul>
                    <todo
                        v-for="(todo, index) in todos"
                        :key="index"
                        :description="todo.description"
                        :completed="todo.completed"
                        @on-toggle="toggleTodo(event)"
                        @on-delete="deleteTodo(todo)"
                        @on-edit="editTodo(todo, $event)"
                    />
                </ul>
            </div>
        </div>
    </div>    
</template>

<script>
import Todo from "./Todo.vue"
import CreateTodo from "./CreateTodo.vue"

export default {
    props: {
        listName: String
    },
    
    components: {
        Todo, 
        CreateTodo
    },

    data() {
        return {
            todos: [
                {description: "Do the dishes", completed:false},
                {description: "Take out the trash", completed:false},
                {description: "Finish doing laundry", completed:false}
            ]
        }
    },

    methods: {
        addTodo(newTodo) {
            this.todos.push({description: newTodo,completed: false})
        },
        toggleTodo(todo) {
            todo.completed = !todo.completed;
        },
        deleteTodo(deletedTodo) {
            this.todos = this.todos.filter(todo => todo !== deletedTodo)
        },
        editTodo(todo, newTodoDescription) {
            todo.description = newTodoDescription
        }
    } 
}
</script>

<style scoped>
    .container {
        width:600px;
        margin: 0 auto;
    }
    .list-name {
        width:100%;
    }
    .list-group {
        display: flex;
        flex-direction: row;
        width:100%;
    }
    ul {
        width:100%;
        padding:0;
    }
</style>