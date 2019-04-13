<template>
    <input type="text" class="form-control search-input" 
            placeholder="Type to search"
            v-model="text"
            v-on:input="onSearchChange"
            >
</template>

<script>
export default {
    name: 'SearchPanel',
    data() {
        return {
            text: ''
        }
    },
    methods: {
        onSearchChange: function() {
            this.$emit('searchChange', this.text);
        }
    },
}
</script>

<style>
    .search-input {
        width: auto;
        flex-grow: 1;
        /* margin-right: 3px; */
    }
</style>
