<template>
    <div class="app-header">
        <h1>My Todo List</h1>
        <h2>Total: {{ total }}, {{ todo }} more to do, {{ done }} done</h2>
    </div>
</template>

<script>
export default {
    name: 'AppHeader',
    props: {
        total: Number,
        todo: Number,
        done: Number
    }
}
</script>