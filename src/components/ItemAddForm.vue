<template>
    <form class="item-add-form d-flex">
        <input class="form-control" placeholder="What needs to be done" v-model="label" />
        <button class="btn btn-outline-secondary" v-on:click.prevent="onLableSubmit">Add Element</button>
        <!--Можно и так можно и в методе --> <!-- <button v-on:click="$emit('labelText', label)">Add</button> -->
    </form>
</template>

<script>
export default {
    name: "ItemAddForm",
    data() {
        return {
            label: ''
        }
    },
    methods: {
        onLableSubmit: function() {
            this.$emit('labelText', this.label);
            this.label = '';
        }
    }
}
</script>

<style>
    .item-add-form {
        margin-top: 10px;
    }

    .item-add-form input {
        margin-right: 3px;
    }
</style>