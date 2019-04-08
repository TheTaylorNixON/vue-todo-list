<template>
    <li>
        <span>{{ todo.label }}</span>
        <button v-on:click="$emit('doneItem', todo.id)">dn</button>
        <button v-on:click="$emit('removeItem', todo.id)">rm</button>
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