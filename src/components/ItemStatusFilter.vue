<template>
    <div class="btn-group">
        <button v-for="(btn, index) in buttons"
                :class="filter === btn.name ? 'btn btn-info' : 'btn btn-outline-secondary' "
                :key="index"
                @click="onBtnClick(btn)" >
                    {{ btn.name }}
        </button>
    </div>
</template>

<script>
export default {
    name: 'ItemStatusFilter',
    data() {
        return {
            buttons: [
                {name: 'All', active: false},
                {name: 'Active', active: false},
                {name: 'Done', active: false}
            ]
        }
    },
    props: ['filter'],
    methods: {
        onBtnClick: function(btn) {
            btn.active = !btn.active;
            this.$emit('statusFilter', btn.name);
        }
    }
}
</script>

<style>

</style>