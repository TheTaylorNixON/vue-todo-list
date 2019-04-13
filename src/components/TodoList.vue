<template>
    <ul class="list-group todo-list">
        <TodoListItem v-for="(todo, index) in todos" 
            :key="index" :todo="todo" 
            v-on:removeItem="removeItem($event)"
            v-on:importantItem="importantItem($event)"
            v-on:doneItem="doneItem($event)"
            />
        <!-- <TodoListItem v-for="(todo, index) in todos" :key="index" :todo="todo" v-on:removeItem="up($event)"/> -->
    </ul>
</template>

<script>
import TodoListItem from './TodoListItem'

export default {
    name: 'TodoList',
    components: {
        TodoListItem
    },
    props: {
        todos: Array
    },
    methods: {
        removeItem: function (id) {
            this.$emit('removeItem', id)
        },
        doneItem: function(id) {
            this.$emit('doneItem', id);
        },
        importantItem: function(id) {
            this.$emit('importantItem', id);
        }
    }
}
</script>

<style>
    .todo-list .list-group-item {
        padding: .25rem .75rem;
    }
</style>