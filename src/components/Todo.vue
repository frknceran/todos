<template>
    <div class="list-group-item">
        <button 
            :class="{ completed }"
            @click="$emit('on-toggle')"
            v-if="!isEditing"
        >
            <span>{{ description }}</span>
        </button>
        <form v-else @submit.prevent="finishEditing()">
            <input 
                type="text"
                v-model="newTodoDescription"
                @blur="finishEditing()"
                ref="newTodo"
            />
        </form>
        <button 
            @click="startEditing()"
        >
            <span class="fa fa-edit"></span>
        </button>
        <button @click="$emit('on-delete')" >
            <span></span>
        </button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            isEditing: false,
            newTodoDescription: ""
        };
    },

    props: {
        description:String,
        completed: Boolean
    },

    methods: {
        startEditing() {
            if(this.isEditing) {
                this.finishEditing();
            } else {
                this.newTodoDescription = this.description
                this.isEditing = true
                this.$nextTick(() => this.$ref.newTodo.focus);
            }
        },
        finisgEditing() {
            this.isEditing = false;
            this.$emit("on-edit", this.newTodoDescription)
        }
    }
}
</script>

<style scoped>
    .list-group-item {
        display:flex;
    }
    .list-group-item button{
        width:100%;
    }
    .completed {
        text-decoration: line-through
    }
</style>