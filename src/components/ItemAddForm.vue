<template>
    <div>
        <input v-model="label" />
        <button v-on:click="onLableSubmit">Add</button>
        <!--Можно и так можно и в методе --> <!-- <button v-on:click="$emit('labelText', label)">Add</button> -->
    </div>
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