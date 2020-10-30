<template>
    <form 
        class="control" 
        @submit.prevent = "AddDoto()"
    >
        <input 
            v-model= "newTodo"
            type="Text"
            placeholder="Create a new to do..."
        />
    </form>
</template>
<script>
export default {

    data() {
        return {
            newTodo: ""
        }
    },

    methods: {
        addTodo() {
            if(this.newTodo.length > 0) {
                this.$emit("on-new-todo", this.todo)
            }
            this.newTodo = "";
        }
    }
}
</script>

<style scoped>
    input {
        width:100%;
    }
</style>