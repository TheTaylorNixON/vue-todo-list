<template>
    <li class="list-group-item">
        <span class="todo-list-item">
            <span class="todo-list-item">{{ todo.label }}</span>
            <button class="btn btn-outline-success btn-sm float-right" 
                    v-on:click="$emit('doneItem', todo.id)">
                    <i class="fa fa-exclamation" />
            </button>
            <button class="btn btn-outline-danger btn-sm float-right" 
                    v-on:click="$emit('removeItem', todo.id)">
                    <i class="fa fa-trash-o" />
            </button>
        </span>
    </li>
</template>

<script>
export default {
    name: 'TodoListItem',
    props: ['todo']
    // props: {
    //     todo: Object
    // }
}
</script>

<style>
    .todo-list-item {
        font-size: 1.25rem;
    }

    .todo-list-item button {
        width: 35px;
        margin: 3px;
    }

    .todo-list-item-label {
        margin-left: 1.25rem;
        line-height: 35px;
        cursor: pointer;
        user-select: none;
    }

    .todo-list-item.done .todo-list-item-label {
        text-decoration: line-through;
    }

    .todo-list-item.important .todo-list-item-label {
        font-weight: bold;
        color: steelblue;
    }

    /* .fa-trash-o:before {
        content: "\f014";
    }

    .fa-exclamation:before {
        content: "\f12a";
    } */
</style>
